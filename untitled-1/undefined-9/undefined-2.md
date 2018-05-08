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



## 상품/지수선물 종목 체결

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/price" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/price
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
     "isuSrtCd": [ " -" 
    ],
     "trdPrc": null,
     "opnprc": null,
     "hgprc": null,
     "lwprc": null,
     "accTrdvol": null,
     "trdTm": null,
     "trdvol": null,
     "lstTrdTpCd": 0,
     "accTrdval": null,
     "fstmmAgndaContrtPrc": null,
     "futrmmAgndaContrtPrc": null,
     "negoBlkAccTrdvol": null,
     "realtmUplmtprc": null,
     "realtmLwlmtprc": null 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수선물 종목 우선호가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/orderbook" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/orderbook
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
     "isuSrtCd": [ " -" 
    ],
     "askStep1BstordPrc": null,
     "askStep2BstordPrc": null,
     "askStep3BstordPrc": null,
     "askStep4BstordPrc": null,
     "askStep5BstordPrc": null,
     "askStep1BstordRqty": null,
     "askStep2BstordRqty": null,
     "askStep3BstordRqty": null,
     "askStep4BstordRqty": null,
     "askStep5BstordRqty": null,
     "bidStep1BstordPrc": null,
     "bidStep2BstordPrc": null,
     "bidStep3BstordPrc": null,
     "bidStep4BstordPrc": null,
     "bidStep5BstordPrc": null,
     "bidStep1BstordRqty": null,
     "bidStep2BstordRqty": null,
     "bidStep3BstordRqty": null,
     "bidStep4BstordRqty": null,
     "bidStep5BstordRqty": null,
     "askTotOrdRqty": null,
     "bidTotOrdRqty": null,
     "askStep1BstordCnt": null,
     "bidStep1BstordCnt": null,
     "askStep2BstordCnt": null,
     "bidStep2BstordCnt": null,
     "askStep3BstordCnt": null,
     "bidStep3BstordCnt": null,
     "askStep4BstordCnt": null,
     "bidStep4BstordCnt": null,
     "askStep5BstordCnt": null,
     "bidStep5BstordCnt": null,
     "askValidOrdCnt": null,
     "bidValidOrdCnt": null,
     "ordAcptTm": null,
     "deemTrdPrc": null 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수선물 종목 일중

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/intraday" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/intraday
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



## 상품/지수선물 종목 히스토리

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/history" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/history
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
ddddd
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



