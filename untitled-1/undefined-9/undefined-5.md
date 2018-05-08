---
description: (조회 방식)
---

# 업종지수 조회

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



## 업종 예상지수

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/prospectindex" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/prospectindex
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
     "deemTm": "9000000",
     "deemTrdPrc": 2471.12,
     "deemAccTrdvol": 15801,
     "deemcmpprevddPrc": 9.74,
     "deemcmpprevddTpCd": "69",
     "deemAccTrdval": 298225 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 업종 시가총액

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/marketcap" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/marketcap
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
     "isuCnt": 1442,
     "accTrdvol": 501479,
     "accTrdval": 6323816,
     "listShrs": 53642471 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 업종별 투자자별

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/investors" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/investors
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
     "Tm": "0",
     "isuSrtCd": "K1",
     "invstLists": [ 
      {
         "invstCd": "0",
         "askTrdvol": 5907489,
         "askTrdval": 302311797,
         "bidTrdvol": 6739796,
         "bidTrdval": 381023826 
      },
      {
         "invstCd": "0",
         "askTrdvol": 2065869,
         "askTrdval": 96146505,
         "bidTrdvol": 2982361,
         "bidTrdval": 122971912 
      },
      ... 이하생략 ...
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 업종 일중

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/intraday" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/intraday
{% endapi-method-summary %}

{% api-method-description %}
상품/지수선물 종목 10초/분별 데이터 제공
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

{% api-method-parameter type="string" name="inddCycleTpCd" required=true %}
일중전송주기구분코드 구분코드 \(10:10초, 60:1분, 600:10분\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqStrtDd" required=true %}
조회시작일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="strtTm" required=true %}
시작시각 \(HHMM\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="endTm" required=true %}
종료시각 \(HHMM\)
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
     "hisLists": [ 
      {
         "inddTm": "9300000",
         "inddOpnprc": 2386.7,
         "inddHgprc": 2388.88,
         "inddLwprc": 2385.62,
         "inddClsprc": 2387.58,
         "inddTrdvol": 53052 
      },
      {
         "inddTm": "9200000",
         "inddOpnprc": 2387.03,
         "inddHgprc": 2388.37,
         "inddLwprc": 2385.86,
         "inddClsprc": 2386.65,
         "inddTrdvol": 42379 
      },
      {
         "inddTm": "9100000",
         "inddOpnprc": 2386.76,
         "inddHgprc": 2388.33,
         "inddLwprc": 2383.47,
         "inddClsprc": 2387.37,
         "inddTrdvol": 29504 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 업종 히스토리

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/history" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/history
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

{% api-method-parameter type="string" name="trnsmCycleTpCd" required=true %}
전송주기구분코드 \(D:일별, W:주별, M:월별\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqStrtDd" required=true %}
조회시작일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqEndDd" required=true %}
조회종료일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="number" name="reqCnt" required=true %}
요청건수 \(최대 100건\)
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
     "hisLists": [ 
      {
         "BzDd": 20170331,
         "trdPrc": 2160.23,
         "cmpprevddTpCd": "5",
         "opnprc": 2166.62,
         "hgprc": 2166.93,
         "lwprc": 2159.8,
         "accTrdvol": 441640,
         "accTrdval": 4479971,
         "cmpprevddPrc": -4.41 
      },
       
      {
         "BzDd": 20170330,
         "trdPrc": 2164.64,
         "cmpprevddTpCd": "5",
         "opnprc": 2170.18,
         "hgprc": 2174.16,
         "lwprc": 2159.16,
         "accTrdvol": 643563,
         "accTrdval": 4574158,
         "cmpprevddPrc": -2.34 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



