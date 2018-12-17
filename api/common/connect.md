# 서비스 연동

오픈플랫폼과 핀테크 서비스 간에 연동을 위해 **금융투자 핀테크 포탈 가입여부 확인 API**와 핀테크 서비스에 연결된 **가상계좌를 조회할 수 있는 API**를 제공합니다. 

계좌기반조회 API를 사용하는 핀테크 서비스의 경우 먼저 이용자가 금융투자 핀테크 포탈에 가입했는지를 API를 통해 확인하고, 미 가입자는 금융투자 핀테크 포탈 가입화면으로 유도해야 합니다. 그리고 사용하려는 증권회사의 계좌번호에 대응되는 가상계좌번호를 발급받아 핀테크서비스에 연결\(핀테크 서비스 신청\)을 수행해야 합니다. 

이미 금융투자 핀테크 포탈에 가입한 이용자는 핀테크서비스에 가상계좌를 연결하였는지를 확인하기 위해 핀테크 서비스 연결 여부 확인 및 가상계좌 리스트 조회 API를 이용하여 설정한 가상계좌가 있는지를 확인하고, 이용자가 원하는 계좌가 추가로 필요하다면 가상계좌발급과 연결을 안내해야 합니다. 

{% hint style="success" %}
서비스연동 API은 [개발자센터-서비스연동](https://developers.koscom.co.kr/documentation/common/member) 에서 이용할 수 있습니다.
{% endhint %}



## 회원 가입 여부 확인

핀테크 서비스 이용자가 금융투자 핀테크 포탈에 가입했는지를 확인하기 위한 API

* **핀테크 서비스 이용자가 오픈플랫폼 회원인지 확인하기 위한 API** 
* 가상계좌번호 발급, 정보제공동의서 작성 등 사전절차 안내 필요 여부 확인用

{% api-method method="post" host="https://{APIGWAddr}/v1/common/member" path="/register/search" %}
{% api-method-summary %}
/register/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" required=true %}
Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "result": "member",
   "commonTermsExpireDate": "20181105" 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Content-Type  \|   `Application/json; charset=utf-8`

#### Authentication  \|  **`API Key`**

#### Request Body Parameters

| **`Name`** | **`Type`** | **`Description`** |
| :--- | :--- | :--- |
| _**partner**_ | _**Object**_ |  |
| comId | String\(5\) | 핀테크 기업 코드 |
| srvId | String\(20\) | 핀테크 서비스 코드 |
| _**commonHeader**_ | _**Object**_ |  |
| reqIdPlatform | String | `사용안함` |
| reqIdConsumer | String\(20\) | `선택` 핀테크기업에서 사용하는 메시지 |
| ci | String\(88\) | 연계정보 |
| _**body**_ | _**Object**_ |  |
| korName | String\(10\) | 한글이름 |

`핀테크기업코드` 및 `핀테크서비스코드`는 이용기관 등록 이후 발급 되며 샌드박스에서 테스트 시에는 임시로 핀테크 기업 코드 `"comId" : "F0995"`, 핀테크 서비스 코드 `"srvId" : "297"`로 테스트 가능

#### Request Body Example

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
    "partner": {
		"comId": "F0995",
		"srvId": "297"
    },
    "commonHeader": {
		"reqIdConsumer": "reqid-0001",
		"ci": "QciuDFKLcwalCKtWALuNWic9eGm7WNdauW+A+n+mpfhif24c3msHdzVjoZK0ntkXZ1+nA6LX47nyKmIq1JoHhg=="
    },
	"body" : {
		"korName": "박환덕"
	}
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Response Body Parameters

| **`Name`** | **`Type`** | **`Description`** |
| :--- | :--- | :--- |
| result | String\(12\) |  회원가입여부 \(member \| nonMember\) |
| commonTermsExpireDate  | String\(8\) |  이용자의 오픈플랫폼 금융정보제동 동의 만료일 |

#### Response Body Example

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
   "result": "member",
   "commonTermsExpireDate": "20181105" 
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 가상계좌 리스트 조회

핀테크 서비스 이용자가 금융투자 핀테크 포탈에서 사용하려는 핀테크 서비스에 연결한 가상계좌리스트를 조회하기 위한 API \(금융거래정보 제3자 제공 동의 계좌\)

* **핀테크 서비스 이용자가 발급받은 가상계좌번호 목록을 금투사 名과 함께 제공**
* 금투사名과 가상계좌목록을 핀테크 서비스 App에 출력하여 이용할 계좌를 간편하게 선택할 수 있도록 함

{% api-method method="post" host="https://{APIGWAddr}/v1/common/member" path="/consent/search" %}
{% api-method-summary %}
/consent/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter type="string" required=true name="Content-Type" %}
Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "vtAccList": [ 
    {
       "comId": "00992",
       "vtAccNo": "160635473367600099",
       "vtAccAlias": "diamond",
       "endpoint": "https://sandbox-apigw.koscom.co.kr/v1/diamond/account/" 
    },
     
    {
       "comId": "00991",
       "vtAccNo": "160613251214500099",
       "vtAccAlias": "cyber",
       "endpoint": "https://sandbox-apigw.koscom.co.kr/v1/cyber/account/" 
    },
     
    {
       "comId": "00993",
       "vtAccNo": "160646584478700099",
       "vtAccAlias": "star",
       "endpoint": "https://sandbox-apigw.koscom.co.kr/v1/star/account/" 
    } 
  ],
   "serviceTermsExpireDate": "20190813" 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

####  Content-Type \| `Application/json` <a id="content-type-or-application-json-charset-utf-8"></a>

#### Authentication \| **`API Key`** <a id="authentication-or-api-key"></a>

#### Request Body Parameters

| **`Name`** | **`Type`** | **`Description`** |
| :--- | :--- | :--- |
| _**partner**_ | _**Object**_ |  |
| comId | String\(5\) | 핀테크 기업 코드 |
| srvId | String\(20\) | 핀테크 서비스 코드 |
| _**commonHeader**_ | _**Object**_ |  |
| reqIdPlatform | String | `사용안함` |
| reqIdConsumer | String\(20\) | `선택` 핀테크기업에서 사용하는 메시지 |
| ci | String\(88\) | 연계정보 |
| _**body**_ | _**Object**_ |  |
| korName | String\(12\) | 한글이름 |

`핀테크 기업 코드` 및 `핀테크 서비스 코드`는 이용기관 등록 이후 발급 되며면 샌드박스에서 테스트 시에는 임시로 핀테크 기업 코드 `"comId" : "F0995"`, 핀테크 서비스 코드 `"srvId" : "297"`로 테스트 가능

**Request Body Example**

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
    "partner": {
		"comId": "F0995",
		"srvId": "297"
    },
    "commonHeader": {
		"reqIdConsumer": "reqid-0001",
		"ci": "QciuDFKLcwalCKtWALuNWic9eGm7WNdauW+A+n+mpfhif24c3msHdzVjoZK0ntkXZ1+nA6LX47nyKmIq1JoHhg=="
    },
	"body" : {
		"korName": "박환덕"
	}
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Response Body Parameters

| **`Name`** | **`Type`** | **`Description`** |
| :--- | :--- | :--- |
| _**vtAccList**_ | _**Array**_ |  |
| comId | String\(5\) | 금융회사코드 |
| vtAccNo | String\(18\) | 가상계좌번호 |
| vtAccAlias | String\(20\) | 가상계좌번호 별칭 |
| serviceTermsExpireDate | String\(8\) | 이용자의 핀테크서비스 금융정보제공동의 만료일 |

#### Response **Body Example**

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
```yaml
{
   "vtAccList": [ 
    {
       "comId": "00992",
       "vtAccNo": "160635473367600099",
       "vtAccAlias": "diamond",
       "endpoint": "https://sandbox-apigw.koscom.co.kr/v1/diamond/account/" 
    },
     
    {
       "comId": "00991",
       "vtAccNo": "160613251214500099",
       "vtAccAlias": "cyber",
       "endpoint": "https://sandbox-apigw.koscom.co.kr/v1/cyber/account/" 
    },
     
    {
       "comId": "00993",
       "vtAccNo": "160646584478700099",
       "vtAccAlias": "star",
       "endpoint": "https://sandbox-apigw.koscom.co.kr/v1/star/account/" 
    } 
  ],
   "serviceTermsExpireDate": "20190813" 
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## 테스트용 목업데이터

* 샌드박스에서 계좌서비스를 테스트 하기 위해서는 미리 제공되는  [계좌서비스 테스트용 ­ 목업 데이터](https://developers.koscom.co.kr/resources/documentation/Account_MockupData_V1.pdf)를 이용하여, 서비스 연동 조회 테스트를 제공한다.

![](../../.gitbook/assets/image%20%2849%29.png)

{% hint style="info" %}
개발자센터  어플리케이션 등록  및  API 테스트\(인증\)  이용방법은 [이곳](https://koscom.gitbook.io/open-api/how-to-use/devcenter) 에서 확인하세요.
{% endhint %}



