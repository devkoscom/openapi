---
description: Server-side Web Application Flow
---

# Authorization Code Grant Flow

이 OAuth 방식은 데이터소유자\(Resource Owner, 서비스 이용자\)에게 데이터 접근에 대한 권한을 위임 받아 `access token`을 오픈플랫폼으로부터 받아오고, 만기\(expiration time\)을 갖는 access token을 갱신\(refresh token\)할 수 있는 권한도 부여 받아 데이터소유자의 승인과정 없이도 API를 통해 데이터에 접근할 수 있는 인증방식입니다.

따라서 주로 서버 사이드의 웹 애플리케이션에서 API를 사용할 경우에 적합하며, 주기적으로 데이터소유자의 위임을 받아 데이터에 접근할 필요가 있는 비즈니스 모델에 사용됩니다.



## 사용 절차

이 방식을 사용하기 위해서는 각종 token, API를 통해 받은 데이터를 안전하게 보관할 수 있는 보안체계가 마련되어야 하며, 데이터접근권한 위임절차 및 동시에 이용자가 위임했던 데이터접근권한을 무효화시키기 위한 수단이 서비스에 마련되어야 합니다.

또한 서비스단말을 통해 authorization code를 받아오고, 그 응답은 애플리케이션 서버로 redirect되기 때문에 핀테크 서비스 사용자 세션정보, authorization code, access token, refresh token 간의 매핑정보 관리 체계를 만들고 보안에 유의해야 합니다.

![Authorization Code Grant Flow](../../../.gitbook/assets/image%20%2817%29.png)

> **Flow** **0 ~ 1      \|    핀테크 서비스 자체 인증 수행**
>
> **Flow 2 ~ 6      \|    Authorization Code 요청과 응답**  
> 데이터소유자의 동의를 통해 authorization code를 받기 위한 flow를 클라이언트 사이드에서 수행하고, 그 결과를 서버 사이드에 구현된 OAuth callback listener로 redirect하는 과정.
>
> **Flow 7 ~ 8      \|    Access Token 요청과 응답**





### **Authorization Code 요청**

> **Flow 2**

HTTP methods    \|   **GET**

Authentication     \|   **OAuth**

End Point              \|   **​https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/authorize​  
                                   https://apigw.koscom.co.kr/auth/oauth/v2/authorize**

Parameters          \|   **`response_type`**=code & **`client_id`**=클라이언트 ID\(API Key\)   
                                  & **`redirect_uri`**=구현된 callback listener 주소 & **`scope`**=지정된 scope   
                                  & **`state`**=돌려받을 opaque value

> `redirect_uri`       :  핀테크 기업의 웹 서버에 구현된 OAuth callback listener 주소이며, 이 값은 최초 서비스 등록 시 입력했던 값과 동일해야 함  
> `scope`                     :  API가 접근하고자 하는 자원 범위  
> `state`                     :  본래 cross-site request forgery\(CSRF\) 공격에 대응하기 위해 사용하나, 대체로 사용자 세션정보를 넣어 authorization code 요청의 응답이 서버로 redirect되었을 때 어느 사용자의 authorization code인지를 구분하기 위해 사용하는 것이 보통임. 요청에 전송했던 값이 응답에 그대로 반환됨

**Example**

```python
​https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/authorize?response_type=code&client_id=l7xxf234248b6fbd42a1a6844861524b2320&redirect_uri=http://localhost:8080/OpenAPITest/callbacknew&scope=test.kiwoom&state=70e86bd5​
```



### 

### **Authorization Code 부여**

> **Flow 3,   Flow 4**

#### '데이터접근위임동의' 에 대한 승인정보 입력 

Flow 2를 요청하면 그 응답으로 Authorization Code를 받아오는 것을 승인할 수 있도록 아래와 같은 권한정보입력 창을 응답으로 내려줍니다.

![&#xAE08;&#xC735;&#xD22C;&#xC790; &#xD540;&#xD14C;&#xD06C;&#xD3EC;&#xD138; &#xB85C;&#xADF8;&#xC778;](../../../.gitbook/assets/image%20%2865%29.png)

핀테크 서비스 이용자가 금융투자 핀테크포털 가입 시 사용했던 아이디와 비밀번호\(또는 OTP\)를 입력하고 로그인 버튼을 누르면, 오픈플랫폼은 이용자가 입력한 정보를 확인하여 정상적인 경우 authorization code를 응답으로 받을 수 있습니다. 비밀번호 또는 OTP가 연속으로 틀린 경우 계정잠김상태로 전환됩니다. 오픈플랫폼 관리자가 비밀번호 초기화 또는 OTP를 초기화할 수 있도록 안내가 필요합니다.



> **Flow 5,   Flow 6**

Flow 3, 4 절차가 정상적으로 수행되면 오픈플랫폼은 authorization code를 응답으로 내려주되, 핀테크 서비스 등록과 Authorization Code 요청 시 지정된 redirect\_uri로 응답을 전달할 수 있도록 http 헤더의 status code를 302로 설정하여 응답을 전송하며, redirect된 응답은 핀테크 서비스 서버 사이드에 구현된 OAuth Callback Listener \(Servlet 등\)로 전달되며, Callback Listener로 유입된 응답 parameter에서 state와 code를 추출하고 누구의 authorization code인지를 확인\(state에 설정한 식별정보 이용\)하여 다음 절차인 access token을 요청합니다.   
에러처리는 [Error Code](https://koscom.gitbook.io/open-api/~/edit/primary/1/error)를 참고하시기 바랍니다.





### **Access Token 요청**

> **Flow 7**

실제 API를 호출할 때 필요한 것은 access token입니다. Access token은 authorization code를 이용하여 요청할 수 있습니다. 

HTTP methods    \|   **POST**

Authentication     \|   **Basic Authorization**

Header                  \|     "**Content-Type**"   :  Application/x-www-form-urlencoded"  
                                     "**authorization**"    :  Basic _Base64\(client\_id:client\_secret\)_

End Point              \|   **​https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/token​  
                                   https://apigw.koscom.co.kr/auth/oauth/v2/token**

Parameters          \|   **`grant_type`**=authorization\_code & **`code`**=할당받은 authorizationcode   
                                  & **`redirect_uri`**=구현된 callback listener 주소

> `code`                        :  Authorization code 요청을 통해 받은 code  
> `redirect_uri`        :  핀테크 기업의 웹 서버에 구현된 OAuth callback listener 주소이며, 이 값은 최초 서비스 등록 시 입력했던 값과 동일해야 함

\*   _Base64\(client\_id:client\_secret\)_     
      client\_id와 client\_secret을 “:”으로 연결하여 base64로 encoding한 값을  위 형식으로 설정





### **Access Token 응답**

> **Flow 8**

Access Token의 응답은 JSON형태로 제공되며 다음의 항목이 포함되어 있으며, 응답은 정상일 경우 status는 200으로 redirection없이 전송됩니다.

| **access token** | API호출시 사용할 access token |
| --- | --- | --- | --- | --- |
| **refresh token** | Access token을 갱신하기 위해 사용되는 token |
| **scope** | Authorization code요청시 지정된 scope |
| **token\_type** | Bearer |
| **expires\_in** | 유효시간 \(초\) |





## API 호출

Access Token발급절차를 통해 받은 access token을 HTTP 헤더 내의 지정된 필드에 포함시켜 API를 호출하면 됩니다.

HTTP methods    \|   **POST**

Authentication     \|   **OAuth**

Header                  \|    "**Authorization**"    :  Bearer _access\_token_  
                                     \*   _access\_token_  : 발급받은 access token

End Point              \|    **​호출하고자 하는 각 API의 endpoint**



**API Request Example**

```yaml
curl -X POST -H "Authorization: Bearer 748c46c8-940f-4eb8-a553-4656253dbac6" -H "Content-Type: application/json" -H "Cache-Control: no-cache"  -d '{
  "accInfo": {
    "vtAccNo": "160657695589800099"
  },
  "balanceRequestBody": {
    "queryType": {
      "assetType": "string",
      "count": 0,
      "page": "string"
    }
  },
  "commonHeader": {
    "ci": "Q9z5ccmjYNrhPVXrdfgfgfFdfgFGHdfg3fGFGgghDFFGghghgSSSfgfgcvbdfgert45rgfgdfgfhpf5vmzjaA==",
    "reqIdConsumer": "string"
  },
  "devInfo": {
    "ipAddr": "IP",
    "macAddr": "string"
  },
  "partner": {
    "comId": "F0000",
    "srvId": "Mock"
  }
}' "https://10.10.10.101:8443/v1/cyber/account/balance/search"

```





## Access Token 갱신 

> Refresh Token 갱신 요

### 1. 요청

Access token 발급 메시지에는 갱신에 사용되는 refresh token \(`refresh_token`\)과 유효시간\(`expires_in`\)이 들어있습니다. 필요에 따라 각 access token이 만료되기 전에 갱신을 요청하면 새로운 access token을 발급받을 수 있습니다. 

{% hint style="danger" %}
Refresh token 기능 지원여부는 비즈니스 모델 및 사용 기업의 신뢰도에 따라 다를 수 있음   
\(이를 고려한 비즈니스 모델은 사전 협의 필요\)
{% endhint %}

HTTP methods    \|   **POST**

Authentication     \|   **Basic Authorization**

Header                  \|     "**Content-Type**"   :  Application/x-www-form-urlencoded"  
                                     "**authorization**"    :  Basic _Base64\(client\_id:client\_secret\)_

End Point              \|   **​https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/token​  
                                   https://apigw.koscom.co.kr/auth/oauth/v2/token**

Parameters          \|   **`grant_type`**=refresh\_token & **`refresh_token`**=발급받은 refresh\_token   
                                   & **`scope`**=지정된 scope

> `refresh_token`      :  access token을 발급받을 때 포함되어 있던 refresh token  
> `scope`                      :  지정된 scope으로 선택항목



### 2. 응답

Access token 요청에 대한 응답과 동일한 형태의 JSON 메시지가 전달됩니다.





## Token Revocation 

### 1. 요청

핀테크 서비스를 구현할 때 반드시 고객이 위임하였던 정보접근권한\(access token, refresh token\)을 무효화할 수 있는 기능을 제공 및 사전 안내해야 하며, 이를 OAuth에서는 Token revocation으로 구현할 수 있습니다. Revocation된 후에 다시 API를 통해 서비스를 재 사용하려면 OAuth 인증 flow를 다시 수행하면 됩니다.  
  
HTTP methods    \|   **POST** or **DELETE**

Authentication     \|   **Basic Authorization**

Header                  \|     "**Content-Type**"   :  Application/x-www-form-urlencoded"  
                                     "**authorization**"    :  Basic _Base64\(client\_id:client\_secret\)_

End Point              \|   **​https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/token/revoke​  
                                   https://apigw.koscom.co.kr/auth/oauth/v2/token/revoke**

Parameters          \|   **`token`**=발급받았던\_token & **`token_type_hint`**=access\_token또는refresh\_token

> `token`                      :  rovoke대상이되는 access token  
> `token_type_hint` :  access\_token,  refresh\_token



### 2. 응답

성공일 경우 JSON형식으로 `{"result": "revoked"}`전송

