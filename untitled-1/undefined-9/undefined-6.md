# 주식 시세조회

주식시장\(유가증권, 코스닥\) 의 종목 리스트, 종목 마스터, 종목 체결, 호가잔량, 종목 투자자별 종가등을 제공한다.



#### URI 입력값

* base URI : [https://sandbox-apigw.koscom.co.kr/v2/market/stocks](https://sandbox-apigw.koscom.co.kr/v2/market/stocks)
* marketcode : 입력가능 marketcode 리스트  \[kospi, kosdaq\]
* issuecode : 주식종목의 단축코드

##  주식종목 리스트 API {#api}

조회대상이 되는 계좌의 실제 잔고 수량, 투자금액 대신 금융투자 상품의 구성비만을 제공함으로써 개인금융정보의 노출부담을 최소화하면서도 투자자산을 기초로 자산통합관리, 자문, 정보제공 등을 받을 수 있도록 하기 위한 API

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/stocks" path="/{marketcode}/lists" %}
{% api-method-summary %}
{marketcode}/lists
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

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

#### Syntax {#syntax}

* URI
  *  /account/portfolio/search
* HTTP methods
  * POST
* Format
  * JSON &lt;application/json; charset=utf-8&gt;
* Content-Type
  * Application/json
* Authentication
  * OAuth 2- Authorization
  * header – Authorization: Bearer 발급받은 access token

#### Example {#example}

Add fileYAML 

```text
{   "partner":{     "comId":"F9999",    "srvId":"999"  },  "commonHeader":{     "reqIdPlatform":"",    "reqIdConsumer":"ID000001",    "ci":"S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="  },  "devInfo":{     "ipAddr":"123451234500",    "macAddr":"7054D27EE247"  },  "accInfo":{       "vtAccNo":"160678007213500001"  },  "portfolioRequestBody":{     "queryType":{       "assetType":"ALL",      "rspType":"RAT",      "count":0,      "page":"null"    }  }}
```

Add fileYAML 

```text
{  "commonHeader":{
```

