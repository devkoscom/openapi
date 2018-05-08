# 옵션 시세조회

상품/지수 옵션시장에 상장된 종목 리스트, 종목 마스터, 종목 체결, 호가 잔량등을 제공한다.



#### URI 입력값

* base URI : [https://sandbox-apigw.koscom.co.kr**/**_**v2/market/options/**_](https://sandbox-apigw.koscom.co.kr/v2/market/stocks/)
* `marketcode `:  ☞ 코드표1  '시장코드표' 참조
* `issuecode `:  예\) KR4101C90009 → K101C9000

#### Syntax

* HTTP methods
  * GET
* Authentication
  * API Key

## 상품/지수옵션 종목 리스트

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/options" path="/{marketcode}/lists" %}
{% api-method-summary %}
 /v2/market/options/{marketcode}/lists
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
       "isuSrtCd": "201N3240",
       "isuCd": "KR4201N32402",
       "isuKorNm": "KOSPI 200 콜옵션 1803 240.0",
       "isuKorAbbr": "K200 옵션 1803 C240.0",
       "map_to": "201N3240*006" 
    },
    {
       "isuSrtCd": "201N3242",
       "isuCd": "KR4201N32428",
       "isuKorNm": "KOSPI 200 콜옵션 1803 242.5",
       "isuKorAbbr": "K200 옵션 1803 C242.5",
       "map_to": "201N3242*006" 
    },
     ... 이하생략...
  ]
}     
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수옵션 종목 마스터

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/options" path="/{marketcode}/{issuecode}/master" %}
{% api-method-summary %}
 /v2/market/ options/{marketcode}/{issuecode}/master
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
     "isuSrtCd": "201N6220",
     "midyyHgstprc": 100.5,
     "midyyHgstprcDd": 20180419,
     "midyyLwstprc": 100.5,
     "midyyLwstprcDd": 20180419,
     "inlistHgstprc": 100.5,
     "inlistHgstprcDd": 20180419,
     "inlistLwstprc": 100.5,
     "inlistLwstprcDd": 20180419,
     "prevddClsprc": 100.95,
     "prevddOpnprc": 100.95,
     "prevddHgprc": 100.95,
     "prevddLwprc": 100.95,
     "prevddAccTrdvol": 0,
     "prevddAccTrdval": 0,
     "prevddOpnintQty": 1,
     "setlPrcTheoPrcDivrgRt": 0,
     "impVolt": 0.1,
     "BzDd": 20180508,
     "basPrc": 97.15,
     "isuKorNm": "KOSPI 200 콜옵션 1806 220.0",
     "isuKorAbbrv": "K200 옵션 1806 C220.0",
     "isuCd": "KR4201N62201",
     "listDd": 20160610,
     "remainDys": 38,
     "cdInt": 1.65,
     "lsttrdDd": 20180614,
     "expDd": 201806,
     "exerPrc": 220,
     "ulyId": "KOSPI200",
     "prcLmtStep1Uplmtprc": 122.45,
     "prcLmtStep2Uplmtprc": 144.6,
     "prcLmtStep3Uplmtprc": 160.45,
     "prcLmtStep1Lwlmtprc": 71.8,
     "prcLmtStep2Lwlmtprc": 49.65,
     "prcLmtStep3Lwlmtprc": 33.8,
     "setlmult": 250000,
     "setlTheoPrc": 0,
     "basTheoPrc": 97.13 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수옵션 종목 종가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/options" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
 /v2/market/options/{marketcode}/{issuecode}/closeprice
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



## 상품/지수옵 종목 체결

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/options" path="/{marketcode}/{issuecode}/price" %}
{% api-method-summary %}
 /v2/market/options/{marketcode}/{issuecode}/price
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
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "201N6220*006",
     "trdPrc": 97.15,
     "opnprc": 0,
     "hgprc": 0,
     "lwprc": 0,
     "accTrdvol": 0,
     "trdTm": 0,
     "trdvol": 0,
     "lstTrdTpCd": 0,
     "accTrdval": 0,
     "isuCd": "KR4201N62201",
     "negoBlkAccTrdvol": 0,
     "realtmUplmtprc": 122.45,
     "realtmLwlmtprc": 71.8 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수옵션 종목 우선호가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/options" path="/{marketcode}/{issuecode}/orderbook" %}
{% api-method-summary %}
 /v2/market/options/{marketcode}/{issuecode}/orderbook
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
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "201N6220",
     "askStep1BstordPrc": 122.35,
     "askStep2BstordPrc": 0,
     "askStep3BstordPrc": 0,
     "askStep4BstordPrc": 0,
     "askStep5BstordPrc": 0,
     "askStep1BstordRqty": 10,
     "askStep2BstordRqty": 0,
     "askStep3BstordRqty": 0,
     "askStep4BstordRqty": 0,
     "askStep5BstordRqty": 0,
     "bidStep1BstordPrc": 71.9,
     "bidStep2BstordPrc": 0,
     "bidStep3BstordPrc": 0,
     "bidStep4BstordPrc": 0,
     "bidStep5BstordPrc": 0,
     "bidStep1BstordRqty": 10,
     "bidStep2BstordRqty": 0,
     "bidStep3BstordRqty": 0,
     "bidStep4BstordRqty": 0,
     "bidStep5BstordRqty": 0,
     "askTotOrdRqty": 10,
     "bidTotOrdRqty": 10,
     "askStep1BstordCnt": 1,
     "bidStep1BstordCnt": 1,
     "askStep2BstordCnt": 0,
     "bidStep2BstordCnt": 0,
     "askStep3BstordCnt": 0,
     "bidStep3BstordCnt": 0,
     "askStep4BstordCnt": 0,
     "bidStep4BstordCnt": 0,
     "askStep5BstordCnt": 0,
     "bidStep5BstordCnt": 0,
     "askValidOrdCnt": 1,
     "bidValidOrdCnt": 1,
     "ordAcptTm": 9012700,
     "deemTrdPrc": 0 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수옵션 종목 일중

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/options" path="/{marketcode}/{issuecode}/intraday" %}
{% api-method-summary %}
 /v2/market/options/{marketcode}/{issuecode}/intraday
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
종목코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inddCycleTpCd" required=true %}
일중전송주기구분코드 구분코드 \(10:10초, 60:1분, 600:10분\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqStrtDd" required=true %}
조회시작일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="strtTm" required=true %}
시작시각 \(HHMMSS\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="endTm" required=true %}
종료시각 \(HHMMSS\)
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수옵션 종목 히스토리

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/options" path="/{marketcode}/{issuecode}/history" %}
{% api-method-summary %}
 /v2/market/options/{marketcode}/{issuecode}/history
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

{% api-method-parameter type="string" name="trnsmCycleTpCd" required=true %}
전송주기구분코드 \(D:일별, W:주별, M:월별\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqStrtDd" required=true %}
조회시작일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqEndDd" required=true %}
조회종료일자 \(YYYYMMDD\_\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="reqCnt" required=true %}
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
     "isuSrtCd": "201N6220",
     "hisLists": [ 
      {
         "BzDd": 20180330,
         "trdPrc": 94.6,
         "cmpprevddTpCd": "0",
         "opnprc": 94.6,
         "hgprc": 94.6,
         "lwprc": 94.6,
         "accTrdvol": 0,
         "accTrdval": 0,
         "opnintQty": 0,
         "cmpprevddPrc": 0 
      },
       
      {
         "BzDd": 20180329,
         "trdPrc": 92.3,
         "cmpprevddTpCd": "0",
         "opnprc": 92.3,
         "hgprc": 92.3,
         "lwprc": 92.3,
         "accTrdvol": 0,
         "accTrdval": 0,
         "opnintQty": 0,
         "cmpprevddPrc": 0 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



