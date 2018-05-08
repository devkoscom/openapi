# 선물 시세조회

#### URI 입력값

* `marketcode `:  ☞ 코드표1  '시장코드표' 참조
* `issuecode `:  예\) KR4101C90009 → K101C9000
  * 종목코드\(issuecode\) 추가:  연결선물코드

     - 선물최근월물의  종목히스토리 조회를 위해  사용가능

     - 현재가 조회시 조회결과 종목코드는 현재     기준 시장에서 거래되는 종목의 단축종목코드로 결과를 보내줌

     - 코드표 -&gt;  '시장코드표' 참조



## 상품/지수선물 종목 리스트

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/lists" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/lists
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "trdDd": "20180307",
   "mktEndTm": "1550",
   "isuLists": [ 
    {
       "isuSrtCd": "105N3000",
       "isuCd": "KR4105N30003",
       "isuKorNm": "MINI KOSPI200 선물 1803",
       "isuKorAbbr": "MINI K200 선물 1803",
       "map_to": "105N3000*103" 
    },
     
    {
       "isuSrtCd": "M2FA001",
       "isuCd": "KR4105N30003",
       "isuKorNm": "MINI KOSPI200 선물 1803",
       "isuKorAbbr": "MINI K200 선물 1803",
       "map_to": "M2FA001" 
    },
     ... 이하생략 ...
  ] 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수선물 종목 마스터

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/master" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/master
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
종목코드
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
     "isuSrtCd": [ " -" 
    ],
     "midyyHgstprc": null,
     "midyyHgstprcDd": null,
     "midyyLwstprc": null,
     "midyyLwstprcDd": null,
     "inlistHgstprc": null,
     "inlistHgstprcDd": null,
     "inlistLwstprc": null,
     "inlistLwstprcDd": null,
     "prevddClsprc": null,
     "prevddOpnprc": null,
     "prevddHgprc": null,
     "prevddLwprc": null,
     "prevddAccTrdvol": null,
     "prevddAccTrdval": null,
     "prevddOpnintQty": null,
     "setlPrcTheoPrcDivrgRt": null,
     "BzDd": 20180504,
     "basPrc": null,
     "isuKorNm": " -",
     "isuKorAbbrv": " -",
     "isuCd": " -",
     "listDd": null,
     "remainDys": null,
     "cdInt": null,
     "lsttrdDd": null,
     "expDd": null,
     "ulyId": " -",
     "prcLmtStep1Uplmtprc": null,
     "prcLmtStep2Uplmtprc": null,
     "prcLmtStep3Uplmtprc": null,
     "prcLmtStep1Lwlmtprc": null,
     "prcLmtStep2Lwlmtprc": null,
     "prcLmtStep3Lwlmtprc": null,
     "opnintLmtQty": null,
     "setlmult": null,
     "setlTheoPrc": null,
     "basTheoPrc": null 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수선물 종목 종가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/closeprice
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
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



## 

