# format sample

KOSPI/KOSDAQ등의 지수 예상지수 및 업종별 투자자별 거래량등을 제공한다.  


####  URI 입력값 {#uri}

* base URI : [https://sandbox-apigw.koscom.co.kr**/**_**v2/market/index/**_](https://sandbox-apigw.koscom.co.kr/v2/market/stocks/)
* `marketcode` : ☞ 코드표 '시장코드표' 참조
* `issuecode` :  ☞ 코드표 '업종코드표' 참조

#### Syntax {#syntax}

* HTTP methods
  * GET
* Authentication
  * API Key

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

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Syntax

* URI

  * /account/balance/search

* HTTP methods

  * POST

* Format

  * JSON &lt;application/json; charset=utf-8&gt;

* Content-Type

  * Application/json

* Authentication
  * OAuth 2- Authorization
  * header – Authorization: Bearer 발급받은 access token

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

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

 



