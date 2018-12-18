# Basic Authentication

Basic Authentication 인증체계를 사용하는 API는 **민감정보가 포함된** 데이터를 전용회선을 사용하는 금융기관에 한정하여 API 요청•응답하는 경우이며, API호출 시 포함되어 전송된 인증 값의 정상 여부를 판단하여 접근을 승인하고 있습니다. 승인과정이 정상적으로 처리되면 오픈플랫폼은 API호출에 필요한 핀테크 서비스는 API를 호출할 때 서비스를 받아주어 해당 금융기관에 전송하게 됩니다. 

### 

### Base64 로 Encoding 하는 방법

1.   `apikey` +  "`:`" + `secret` 값을 결합하여 string 생성
2.   생성된 string을 base64 encoding 함
3.   'Basic' + encode string 을 결합하여 Authorization의 인자 값으로 사용함    **\***   `apikey`및 `secret` **:**  개발자 센터에서 앱 성생 시 발급되는 고유 정보

{% code-tabs %}
{% code-tabs-item title="Authorization Value Example" %}
```swift
Basic Qwsxxxxf1D34A5fdsdassdeerf234248b6fbd42a1a6844861524b2320
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="Header Authorization Code Example" %}
```yaml
headers: {
    'Authorization': 'Basic' + new Buffer(apikey + ':' + secret).toString('base64')
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}



### POST 방식

HTTP header의 authorization 필드에 값을 넣어 전송

```yaml
curl -X POST -H "comId:00995” –H 
“authorization:Basic Qwsxxxxf1D34A5fdsdassdeerf234248b6fbd42a1a6844861524b2320” -H 
"Content-Type: application/json" -H
 -d '{
  "partner": {
    "comId": "COMPANY-ID",
    "srvId": "CLIENT-ID"
  },
  "commonHeader": {
    "reqIdPlatform": "android",
    "reqIdConsumer": "tx-001",
    "certDn": “null”,
    "ci": "null"
  },
  "contractRequestBody": {
    "count”: 0,
    “page”: ”null”
  }
}' "https://sandbox-apigw.koscom.co.kr/v1/account/accountlist/search"
```





