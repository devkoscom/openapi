---
description: 서비스 연동 API
---

# 연동

오픈플랫폼과 핀테크 서비스 간에 연동을 위해 **금융투자 핀테크 포탈 가입여부 확인 API**와 핀테크 서비스에 연결된 **가상계좌를 조회할 수 있는 API**를 제공합니다. 

계좌기반조회 API를 사용하는 핀테크 서비스의 경우 먼저 이용자가 금융투자 핀테크 포탈에 가입했는지를 API를 통해 확인하고, 미 가입자는 금융투자 핀테크 포탈 가입화면으로 유도해야 합니다. 그리고 사용하려는 증권회사의 계좌번호에 대응되는 가상계좌번호를 발급받아 핀테크서비스에 연결\(핀테크 서비스 신청\)을 수행해야 합니다. 

이미 금융투자 핀테크 포탈에 가입한 이용자는 핀테크서비스에 가상계좌를 연결하였는지를 확인하기 위해 핀테크 서비스 연결 여부 확인 및 가상계좌 리스트 조회 API를 이용하여 설정한 가상계좌가 있는지를 확인하고, 이용자가 원하는 계좌가 추가로 필요하다면 가상계좌발급과 연결을 안내해야 합니다. 

{% hint style="success" %}
서비스연동 API에 대한 **자세한 설명**과** 사용방법**은 아래의 [링크](https://developers.koscom.co.kr/documentation/common/member#!method_0_0_operation_0_content)를 클릭하면 이용할 수 있습니다:

[개발자센터-서비스연동API](https://developers.koscom.co.kr/documentation/common/member)
{% endhint %}





## 금융투자 핀테크 포탈 가입 여부 확인 API

핀테크 서비스 이용자가 금융투자 핀테크 포탈에 가입했는지를 확인하기 위한 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/common/member" path="/register/search" %}
{% api-method-summary %}
/register/search
{% endapi-method-summary %}

{% api-method-description %}
Request Body 
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

```
{
  "result": "member"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Syntax

* URI

  * https://apigw.koscom.co.kr/v1/common/member/register/search
  * https://sandbox-apigw.koscom.co.kr/v1/common/member/ register/search

* HTTP methods

  * POST

* Format

  * JSON &lt;application/json; charset=utf-8&gt;

* Content-Type

  * Application/json

* Authentication
  * API Key
  * header – apikey: 발급받은 API key

#### Example

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

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
```yaml
{
  "result": "member"
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

자세한 포맷은 [개발자센터 ](https://developers.koscom.co.kr/documentation/common/member)또는 [공식매뉴얼](https://developers.koscom.co.kr/documentation/reference) 에서 확인하세요.





## 핀테크 앱 사용 신청 여부 확인 및 가상계좌 리스트 조회 API

핀테크 서비스 이용자가 금융투자 핀테크 포탈에서 사용하려는 핀테크 서비스에 연결한 가상계좌리스트를 조회하기 위한 API \(금융거래정보 제3자 제공 동의 계좌\)

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/common/member" path="/consent/search" %}
{% api-method-summary %}
/consent/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
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

#### Syntax

* URI

  * https://apigw.koscom.co.kr/v1/common/member/consent/search
  * https://sandbox-apigw.koscom.co.kr/v1/common/member/consent/search

* HTTP methods

  * POST

* Format

  * JSON &lt;application/json; charset=utf-8&gt;

* Content-Type

  * Application/json

* Authentication
  * API Key
  * header – apikey: 발급받은 API key

 **Example**

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

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

 자세한 포맷은 [개발자센터](https://developers.koscom.co.kr/documentation/common/member) 또는 [공식매뉴얼](https://developers.koscom.co.kr/documentation/reference) 에서 확인하세요.

