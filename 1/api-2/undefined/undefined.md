---
description: 서비스연동 API
---

# 서비스연동

오픈플랫폼과 핀테크 서비스 간에 연동을 위해 **금융투자 핀테크 포탈 가입여부 확인 API**와 핀테크 서비스에 연결된 **가상계좌를 조회할 수 있는 API**를 제공합니다. 

계좌기반조회 API를 사용하는 핀테크 서비스의 경우 먼저 이용자가 금융투자 핀테크 포탈에 가입했는지를 API를 통해 확인하고, 미 가입자는 금융투자 핀테크 포탈 가입화면으로 유도해야 합니다. 그리고 사용하려는 증권회사의 계좌번호에 대응되는 가상계좌번호를 발급받아 핀테크서비스에 연결\(핀테크 서비스 신청\)을 수행해야 합니다. 

이미 금융투자 핀테크 포탈에 가입한 이용자는 핀테크서비스에 가상계좌를 연결하였는지를 확인하기 위해 핀테크 서비스 연결 여부 확인 및 가상계좌 리스트 조회 API를 이용하여 설정한 가상계좌가 있는지를 확인하고, 이용자가 원하는 계좌가 추가로 필요하다면 가상계좌발급과 연결을 안내해야 합니다. 

{% hint style="success" %}
서비스연동 API는 [개발자센터-서비스연동 API](https://developers.koscom.co.kr/documentation/common/member)에서 이용하실 수 있습니다.
{% endhint %}



#### Syntax {#syntax}

* HTTP methods
  * **POST**
* Authentication
  * **API Key**
* URI
  * https://apigw.koscom.co.kr/v1/common/member/
  * https://sandbox-apigw.koscom.co.kr/v1/common/member/ 



## 금융투자 핀테크 포탈 가입 여부 확인 API

핀테크 서비스 이용자가 금융투자 핀테크 포탈에 가입했는지를 확인하기 위한 API

{% api-method method="post" host="" path="/register/search" %}
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

{% api-method-body-parameters %}
{% api-method-parameter name="partner" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="commonHeader" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="body" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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
| comId | string\(5\) | 핀테크 기업 코드 |  |
| srvId | string\(20\) | 핀테크 서비스 코드 |  |
| reqIdPlatform | string | . | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | 선택 |
| ci | string\(88\) | 연계정보 88byte |  |
| korName | string\(10\) | 한글이름 |  |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- |
| result | string\(12\) | 가입여부 member \| nonMember |  |



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
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
 Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="partner" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="commonHeader" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="body" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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
| comId | string\(5\) | 핀테크 기업 코드 |  |
| srvId | string\(20\) | 핀테크 서비스 코드 |  |
| reqIdPlatform | string | . | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | 선택 |
| ci | string\(88\) | 연계정보 88byte |  |
| korName | string\(10\) | 한글이름 |  |

#### Response Parameters

| **Name** | **Type** | **Description** |
| --- | --- | --- | --- | --- |
| vtAccList | Array | 가상계좌번호 묶음 \(배열로 반복\) |
| comId | String\(5\) | 금융회사 코드 |
| vtAccNo | String\(18\) | 가상계좌번호 |
| vtAccAlias | String\(20\) | 가상계좌번호 별칭 |



