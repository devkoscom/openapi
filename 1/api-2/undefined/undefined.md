# 서비스연동

오픈플랫폼과 핀테크 서비스 간에 연동을 위해 **금융투자 핀테크 포탈 가입여부 확인 API**와 핀테크 서비스에 연결된 **가상계좌를 조회할 수 있는 API**를 제공합니다. 

계좌기반조회 API를 사용하는 핀테크 서비스의 경우 먼저 이용자가 금융투자 핀테크 포탈에 가입했는지를 API를 통해 확인하고, 미 가입자는 금융투자 핀테크 포탈 가입화면으로 유도해야 합니다. 그리고 사용하려는 증권회사의 계좌번호에 대응되는 가상계좌번호를 발급받아 핀테크서비스에 연결\(핀테크 서비스 신청\)을 수행해야 합니다. 

이미 금융투자 핀테크 포탈에 가입한 이용자는 핀테크서비스에 가상계좌를 연결하였는지를 확인하기 위해 핀테크 서비스 연결 여부 확인 및 가상계좌 리스트 조회 API를 이용하여 설정한 가상계좌가 있는지를 확인하고, 이용자가 원하는 계좌가 추가로 필요하다면 가상계좌발급과 연결을 안내해야 합니다. 

{% hint style="success" %}
서비스연동 API은 [개발자센터-서비스연동](https://developers.koscom.co.kr/documentation/common/member) 에서 이용할 수 있습니다.
{% endhint %}



## Syntax

HTTP methods    \|   **POST**

Authentication     \|   **API Key**



## 금융투자 핀테크 포탈 가입 여부 확인 API

핀테크 서비스 이용자가 금융투자 핀테크 포탈에 가입했는지를 확인하기 위한 API

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
  "result": "member"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{  
   "partner":{  
      "comId":"F9999",
      "srvId":"999"
   },
   "commonHeader":{  
      "reqIdPlatform":"",
      "reqIdConsumer":"fsfsfshi23",
      "ci":"Q9z5ccmjYNrhPVXrdfgfgfFdfgFGHdfg3fGFGgghDFFGghghgSSSfgfgcvbdfgert45rgfgdfgfhpf5vmzjaA=="
   },
   "body":{  
      "korName":"홍길동"
   }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Request Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- |
| comId | String\(5\) | 핀테크기업코드 |  |
| srvId | String\(20\) | 핀테크서비스코드 |  |
| reqIdPlatform | String | . | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크기업에서 사용하는 메시지 | 선택 |
| ci | String\(88\) | 연계정보 |  |
| korName | String\(10\) | 한글이름 |  |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- |
| result | String\(12\) | 회원가입여부 | member \| nonMember |





## 핀테크 앱 사용 신청 여부 확인 및 가상계좌 리스트 조회 API

핀테크 서비스 이용자가 금융투자 핀테크 포탈에서 사용하려는 핀테크 서비스에 연결한 가상계좌리스트를 조회하기 위한 API \(금융거래정보 제3자 제공 동의 계좌\)

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
   "vtAccList":[  
      {  
         "comId": " 00002",
         "vtAccNo":"160657695589800099",
         "vtAccAlias":"주식투자용"
      },
      {  
         "comId":" 00002",
         "vtAccNo":"160657695589800099",
         "vtAccAlias":"펀드투자용"
      }
   ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

 **Request Example**

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{  
   "partner":{  
      "comId":"F9999",
      "srvId":"999"
   },
   "commonHeader":{  
      "reqIdPlatform":"",
      "reqIdConsumer":"fsfsfshi23",
      "ci":"Q9z5ccmjYNrhPVXrdfgfgfFdfgFGHdfg3fGFGgghDFFGghghgSSSfgfgcvbdfgert45rgfgdfgfhpf5vmzjaA=="
   },
   "body":{  
      "korName":"홍길동"
   }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Request Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- |
| comId | String\(5\) | 핀테크기업코드 |  |
| srvId | String\(20\) | 핀테크서비스코드 |  |
| reqIdPlatform | String | . | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크기업에서 사용하는 메시지 | 선택 |
| ci | String\(88\) | 연계정보 |  |
| korName | String\(12\) | 한글이름 |  |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- |
| comId | String\(5\) | 금융회사코드 |  |
| vtAccNo | String\(18\) | 가상계좌번호 |  |
| vtAccAlias | String\(20\) | 가상계좌번호 별칭 |  |



{% hint style="info" %}
개발자센터  어플리케이션 등록  및  API 테스트\(인증\)  이용방법은 [이곳](https://koscom.gitbook.io/open-api/1/undefined-4/undefined-2) 에서 확인하세요.
{% endhint %}



