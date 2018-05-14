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

## 업종 지수

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/index" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/index
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
업종코드 ex\) K1
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "trdPrc": 2469.21,
     "cmpprevddTpCd": "2",
     "accTrdvol": 494710,
     "trdTm": 13063000,
     "accTrdval": 6246486,
     "cmpprevddPrc": 7.83 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 2. POST 방식

