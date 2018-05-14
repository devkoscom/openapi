# format sample

KOSPI/KOSDAQ등의 지수 예상지수 및 업종별 투자자별 거래량등을 제공한다.  


#### Syntax {#syntax}

* HTTP methods
  * **GET**
* Authentication
  * **API Key**

{% hint style="info" %}
업종지수  스트리밍 조회는 xx를 참고하세요.
{% endhint %}



## 1. GET 방식

## 업종 종가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/closeprice
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" required=true name="issuecode" %}
업종코드 ex\) K1
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
ddddd
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





## 2. POST 방식





ㅇㅇㅇㅇㅇ





## 계좌잔고 조회 API

조회대상이 되는 계좌의 실제 잔고 수량, 손익, 수익률 등을 상세히 조회하기 위한 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/account" path="/balance/search" %}
{% api-method-summary %}
/account/balance/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter type="string" name="Authorization" required=true %}
발급받은 Bearer token \(Access token\)
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="accInfo" type="string" required=true %}
 요청메세지 본문
{% endapi-method-parameter %}

{% api-method-parameter name="partner" type="object" required=true %}
 핀테크 서비스 정보
{% endapi-method-parameter %}

{% api-method-parameter name="commonHeader" type="object" required=true %}
 요청 메세지 제어 헤더 
{% endapi-method-parameter %}

{% api-method-parameter name="devInfo" type="object" required=true %}
 .
{% endapi-method-parameter %}

{% api-method-parameter name="balanceRequestBody" type="object" required=true %}
 .
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{ 
  "commonHeader":{ 
    "reqIdPlatform":"fagbbs22321",
    "reqIdConsumer":" ID00002",
    "certDn":"",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
"accInfo":{ 
"realAccNo":"",
      "vtAccNo":"160678007213500001"
  },
  "balanceResponseBody":{ 
    "queryType":{ 
      "assetType":"ALL",
      "count":"0",
      "page":"null"
    },
    "queryResult":{ 
      "totalCnt":157.0,
      "count":157.0,
      "page":"null"
    }
  },
  "balanceList":{ 
    "balance":{ 
        "summary":{ 
          "cashBalance":6976542.0,
          "d1":6976542.0,
          "d2":6976542.0,
          "substitute":9.816358E7,
          "receivable":0.0,]
          
          dddddddd
          
          "cashAvWithdraw":6976542.0
      }
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
    "reqIdConsumer":"ID00002",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "devInfo":{ 
    "ipAddr":"123451234500",
    "macAddr":"7054D27EE247"
  },
  "accInfo":{ 
      "vtAccNo":"160678007213500001"
   },
  "balanceRequestBody":{ 
    "queryType":{ 
      "assetType":"ALL",
      "count":0,
      "page":"null"
    }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}



#### Request Parameters

| **Name** | **Type** | **Description** |
| --- | --- | --- | --- | --- |
| fundcode | String\(20\) | 펀드표준코드 |
| fundName | Number | 펀드이름 |
| valAtTrade |  |  다음 page를 지시하는 키로 첫 요청은 null\(“null”\)로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청하며, ALL인 경우는 page없이 일괄전송이므로 본 필드는 의미 없음 |
| varAtCur |  | 잔고구분 \[\* 테이블하단참고\] |

> * varAtCur : 잔고구분
>   * NRM\(일반/현금\), CRD\(신용\), LOAN\(대출\), SUM  \(분류가 불가한 경우 구분 없이 합산한 경우며 대출잔고는 제외\)



#### Response Parameters

| **Name** | **Type** | **Description** |
| --- | --- | --- | --- | --- |
| fundcode | String\(20\) | 펀드표준코드 |
| fundName | Number | 펀드이름 |
| valAtTrade | Number | 펀드이름 |
| varAtCur | Number | 펀드이름 |



