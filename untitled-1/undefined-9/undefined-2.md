# 선물 시세조회

상품/지수 선물시장에 상장된 종목 리스트, 종목 마스터, 종목 체결, 호가 잔량등을 제공한다.



## Syntax

HTTP methods    \|   **GET**

Authentication     \|   **API Key**



{% hint style="warning" %}
`marketcode` 및 `issuecode` 는 [코드표 &gt; "시장코드표"](https://koscom.gitbook.io/open-api/untitled-1/undefined-8#undefined)를 참조하세요.
{% endhint %}





## 상품/지수선물 종목 리스트

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/lists" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/lists
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- |
| trdDd | String\(8\) | 체결일자, 거래일자, 매매일자 | YYYYMMDD |
| isuLists | Array\(4\) | 종목리스트 |  |
| isuCd | String\(12\) | 종목코드 |  |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuKorNm | String\(80\) | 종목한글명 |  |
| isuKorAbbrv | String\(40\) | 종목한글약명 | 가나다 |





## 상품/지수선물 종목 마스터

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/master" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/master
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

#### Response Parameters

| **Name** | **Type** | **Description** | ​ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| trdDd | string\(8\) | 체결일자, 거래일자, 매매일자 | YYYYMMDD |
| isuCd | string\(12\) | 종목코드 | ​ |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuKorNm | string\(80\) | 종목한글명 |  |
| isuKorAbbrv | string\(40\) | 종목한글약명 | 가나다 |
| listDd | string\(8\) | 상장일자 | YYYYMMDD |
| prcLmtStep1Uplmtprc | number\(12\) | 가격제한1단계상한가 |  |
| prcLmtStep1Lwlmtprc | number\(12\) | 가격제한1단계하한가 |  |
| prcLmtStep2Uplmtprc | number\(12\) | 가격제한2단계상한가 |  |
| prcLmtStep2Lwlmtprc | number\(12\) | 가격제한2단계하한가 |  |
| prcLmtStep3Uplmtprc | number\(12\) | 가격제한3단계상한가 |  |
| prcLmtStep3Lwlmtprc | number\(12\) | 가격제한3단계하한가 |  |
| basPrc | number\(11\) | 기준가격,기준가액 |  |
| ulyId | string\(3\) | 기초자산명 |  |
| lsttrdDd | string\(8\) | 최종거래일자 |  |
| expDd | string\(8\) | 만기년월 | 권리행사 가능한 만기년월 |
| 업종 | number\(22\) | 거래승수 | 약정대금 및 결제시 사용하는 계산승수 |
| remainDys | number\(8\) | 잔존일수 |  |
| setlTheoPrc | number\(16\) | 정산이론가격 |  |
| basTheoPrc | number\(16\) | 기준이론가격 |  |
| prevddClsprc | number\(11\) | 전일종가 |  |
| prevddOpnprc | number\(11\) | 전일시가 |  |
| prevddHgprc | number\(11\) | 전일고가 |  |
| prevddLwprc | number\(11\) | 전일저가 |  |
| setlPrcTheoPrcDivrgRt | number\(13\) | 정산가격이론가격괴리율 |  |
| prevddOpnintQty | number\(12\) | 전일미결제약정수량 |  |
| inlistHgstprc | number\(11\) | 상장중최고가 |  |
| inlistLwstprc | number\(11\) | 상장중최저가 |  |
| midyyHgstprc | number\(11\) | 연중최고가 |  |
| midyyLwstprc | number\(11\) | 연중최저가 |  |
| inlistHgstprcDd | string\(8\) | 상장중최고가일자 |  |
| inlistLwstprcDd | string\(8\) | 상장중최저가일자 |  |
| midyyHgstprcDd | string\(8\) | 연중최고가일자 |  |
| midyyLwstprcDd | string\(8\) | 연중최저가일자 |  |
| prevddAccTrdvol | number\(15\) | 전일체결수량,전일거래량 |  |
| prevddAccTrdval | number\(22\) | 전일거래대금 |  |
| cdInt | number\(7\) | CD금리 | 예\) 999.999 |
| opnintLmtQty | number\(15\) | 미결제한도수량 | 적용일에 적용되는 상품의 계좌별  미결제 한도 계약수./ 미결제 한도가 적용되지 않은 상품은 0/ 주식선물에만 해당 |





## 상품/지수선물 종가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/closeprice
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | String\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 |  |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |





## 상품/지수선물 체결

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/price" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/price
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter name="issuecode" type="string" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | string\(12\) | 종목단축코드 | 표준코드 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 |  |
| trdvol | number\(10\) | 체결수량, 거래량 | 단위:주 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 일반체결수량+협의대량체결수량+EFP누적체결수량 /2009.08.31 |
| accTrdval | number\(22\) | 누적거래대금 | 일반체결대금+협의대량체결대금+EFP누적체결대금 /2009.08.31 |
| negoBlkAccTrdvol | number\(12\) | 협의대량누적체결수량 |  |
| lstAskbidTpCd | string\(1\) | 최종매도매수구분코드 | 1:매도, 2:매수 \(최종으로 들어온 호가의 매도매수구분값\) |
| trdTm | string\(8\) | 체결시각,거래시각 |  |
| fstmmAgndaContrtPrc | number\(11\) | 최근월물의제약정가격 |  |
| futrmmAgndaContrtPrc | number\(11\) | 원월물의제약정가격 |  |
| realtmUplmtprc | number\(11\) | 실시간상한가 |  |
| realtmLwlmtprc | number\(11\) | 실시간하한가 |  |





## 상품/지수선물 우선호가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/orderbook" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/orderbook
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="marketcode" required=true type="string" %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter name="issuecode" required=true type="string" %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | String\(12\) | 종목단축코드 | 단축코드 |
| bidTotOrdRqty | number\(12\) | 매수총호가잔량 |  |
| bidStep1BstordPrc | number\(11\) | 매수1단계우선호가가격 |  |
| bidStep1BstordRqty | number\(12\) | 매수1단계우선호가잔량 |  |
| bidStep2BstordPrc | number\(11\) | 매수2단계우선호가가격 |  |
| bidStep2BstordRqty | number\(12\) | 매수2단계우선호가잔량 |  |
| bidStep3BstordPrc | number\(11\) | 매수3단계우선호가가격 |  |
| bidStep3BstordRqty | number\(12\) | 매수3단계우선호가잔량 |  |
| bidStep4BstordPrc | number\(11\) | 매수4단계우선호가가격 |  |
| bidStep4BstordRqty | number\(12\) | 매수4단계우선호가잔량 |  |
| bidStep5BstordPrc | number\(11\) | 매수5단계우선호가가격 |  |
| bidStep5BstordRqty | number\(12\) | 매수5단계우선호가잔량 |  |
| askTotOrdRqty | number\(12\) | 매도총호가잔량 |  |
| askStep1BstordPrc | number\(11\) | 매도1단계우선호가가격 |  |
| askStep1BstordRqty | number\(12\) | 매도1단계우선호가잔량 |  |
| askStep2BstordPrc | number\(11\) | 매도2단계우선호가가격 |  |
| askStep2BstordRqty | number\(12\) | 매도2단계우선호가잔량 |  |
| askStep3BstordPrc | number\(11\) | 매도3단계우선호가가격 |  |
| askStep3BstordRqty | number\(12\) | 매도3단계우선호가잔량 |  |
| askStep4BstordPrc | number\(11\) | 매도4단계우선호가가격 |  |
| askStep4BstordRqty | number\(12\) | 매도4단계우선호가잔량 |  |
| askStep5BstordPrc | number\(11\) | 매도5단계우선호가가격 |  |
| askStep5BstordRqty | number\(12\) | 매도5단계우선호가잔량 |  |
| bidValidOrdCnt | number\(11\) | 매수유효호가건수 |  |
| bidStep1BstordCnt | number\(11\) | 매수1단계우선호가건수 |  |
| bidStep2BstordCnt | number\(11\) | 매수2단계우선호가건수 |  |
| bidStep3BstordCnt | number\(11\) | 매수3단계우선호가건수 |  |
| bidStep4BstordCnt | number\(11\) | 매수4단계우선호가건수 |  |
| bidStep5BstordCnt | number\(11\) | 매수5단계우선호가건수 |  |
| askValidOrdCnt | number\(11\) | 매도유효호가건수 |  |
| askStep1BstordCnt | number\(11\) | 매도1단계우선호가건수 |  |
| askStep2BstordCnt | number\(11\) | 매도2단계우선호가건수 |  |
| askStep1BstordCnt | number\(11\) | 매도3단계우선호가건수 |  |
| askStep1BstordCnt | number\(11\) | 매도4단계우선호가건수 |  |
| askStep1BstordCnt | number\(11\) | 매도5단계우선호가건수 |  |
| ordAcptTm | number\(11\) | 호가접수시각 |  |
| deemTrdPrc | number\(11\) | 예상체결가격 |  |





## 상품/지수선물 일중

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/intraday" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/intraday
{% endapi-method-summary %}

{% api-method-description %}
상품/지수선물 종목 10초/분별 데이터 제공 \(최대 100건까지 조회가능\)
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter type="string" name="inddCycleTpCd" required=true %}
일중전송주기구분코드 구분코드 \(10:10초, 60:1분, 600:10분\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqStrtDd" required=false %}
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuNm | String\(80\) | 종목명 |  |
| hisLists | Array\(4\) | 과거리스트 |  |
| inddTm | string\(8\) | 일중시간 | HH:MM:SS |
| inddOpnprc | number\(11\) | 일중시가 | 일중데이타\(10초, 1분, 10분\) |
| inddHgprc | number\(11\) | 일중고가 | 일중데이타\(10초, 1분, 10분\) |
| inddLwprc | number\(11\) | 일중저가 | 일중데이타\(10초, 1분, 10분\) |
| inddClsprc | number\(11\) | 일중종가 | 일중데이타\(10초, 1분, 10분\) |
| inddTrdvol | number\(11\) | 일중거래량 | 일중데이타\(10초, 1분, 10분\) |





## 상품/지수선물 종목 히스토리

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/history" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/history
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter name="issuecode" type="string" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter type="string" name="trnsmCycleTpCd" required=true %}
전송주기구분코드 \(D:일별, W:주별, M:월별\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqStrtDd" required=true %}
조회시작일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqEndDd" required=true %}
조회종료일자 \(YYYYMMDD\_\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="reqCnt" required=false %}
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuNm | String\(80\) | 종목명 |  |
| hisLists | Array\(4\) | 과거리스트 |  |
| trdDd | string\(8\) | 체결일자,거래일자,매매일자 | YYYYMMDD |
| trdPrc | number\(11\) | 체결가격 |  |
| cmpprevddTpCd | string\(1\) | 전일대비부호 |  |
| cmpprevddPrc | number\(11\) | 전일대비가격 |  |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 |  |
| accTrdval | number\(22\) | 누적거래대금 |  |
| opnprc | number\(11\) | 시가 |  |
| hgprc | number\(11\) | 고가 |  |
| lwprc | number\(11\) | 저가 |  |
| opnintQty | number\(10\) | 미결제약정수량 |  |

