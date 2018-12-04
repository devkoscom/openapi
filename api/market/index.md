# 업종지수 조회

KOSPI/KOSDAQ등의 지수 예상지수 및 업종별 투자자별 거래량등을 제공한다.



## Syntax

HTTP methods    \|   **GET**

Authentication     \|   **API Key**



{% hint style="success" %}
`marketcode` 및 `issuecode` 는 [코드표 &gt; "시장코드표"](https://koscom.gitbook.io/open-api/api/market/codetable)를 참조하세요.
{% endhint %}

{% hint style="info" %}
업종지수 스트리밍 조회는 xx를 참고하세요.
{% endhint %}





## 업종 종가

{% api-method method="get" host="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/closeprice
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
업종코드 ex\) K1
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
     "isuSrtCd": "K1",
     "isuCnt": 891,
     "trdPrc": 2409.03,
     "cmpprevddTpCd": "5",
     "opnprc": 2446.81,
     "hgprc": 2449.88,
     "lwprc": 2399.58,
     "accTrdvol": 575922,
     "accTrdval": 8999465,
     "mktcap": 1609052294,
     "cmpprevddPrc": -48.22,
     "listShrs": 53713300 
  } 
}
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
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | String\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 |  |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |
| isuCnt | number\(16\) | 종목수 |  |
| listShrs | number\(16\) | 상장주식수,상장증권수 | 업종상장주식수 단위는  천주, 그외는 1주 |
| mktcap | number\(22\) | 시가총액 | 단위: 업종-백만 |





## 업종 지수

{% api-method method="get" host="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/index" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/index
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
업종코드 ex\) K1
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(3\) | 업종코드 | 업종코드표 참조 |
| trdTm | String\(8\) | 체결시각,거래시각 | \*테이블 하단 참고 |
| trdPrc | number\(10\) | 지수 |  |
| cmpprevddTpCd | String\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비지수 |  |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |

> `trdTm`  
> "HHMMSSmm" 형태로 시간전송  
>    - 정규장 개시전 또는 정규장 체결 발생 이전 : 0  
>    - 장운영시그널, 대량체결 포함  
> _※ 장운영시그널_  
> 정규장마감\(15:00\):31000000 /장종료시간외마감\(15:30\):41000000 /단일가마감\(18:00\):81000000 /일반Buy-in마감\(18:00\):91000007 /당일Buy-in마감\(18:00\):91000008  
> _※ 대량체결시_   
> 장전대량매매체결:51000000/장중대량매매체결:61000000/장후대량매매체결:71000000"





## 업종 예상지수

{% api-method method="get" host="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/prospectindex" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/prospectindex
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
업종코드 ex\) K1
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(3\) | 업종코드 | 업종코드표 참조 |
| deemTm | String\(8\) | 예상체결시각 | HHMMSSmm |
| deemTrdPrc | number\(10\) | 예상지수 |  |
| deemcmpprevddTpCd | String\(1\) | 예상전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| deemcmpprevddPrc | number\(11\) | 예상전일대비지수 |  |
| deemAccTrdvol | number\(12\) | 예상누적체결수량 | 단위:주 |
| deemAccTrdval | number\(22\) | 예상누적거래대금 | 단위:원 |





## 업종 시가총액

{% api-method method="get" host="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/marketcap" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/marketcap
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
업종코드 ex\) K1
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(3\) | 업종코드 |  |
| isuCnt | number\(16\) | 종목수 |  |
| listShrs | number\(16\) | 상장주식수,상장증권수 | 업종상장주식수 단위는  천주, 그외는 1주 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |
| mktcap | number\(22\) | 시가총액 | 단위: 업종-백만 |





## 업종별 투자자별

{% api-method method="get" host="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/investors" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/investors
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
업종코드 ex\) K1
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| Tm | string\(8\) | 장시간 | HHMMSSmm |
| invstLists | Array\(4\) | 투자자리스트 |  |
| invstCd | string\(4\) | 투자자코드 | '투자자코드표' 참조 |
| askTrdvol | number\(10\) | 매도체결수량,매도거래량 |  |
| askTrdval | number\(22\) | 매도거래대금 |  |
| bidTrdvol | number\(10\) | 매수체결수량,매수거래량 |  |
| bidTrdval | number\(22\) | 매수거래대금 |  |





## 업종 일중

{% api-method method="get" host="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/intraday" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/intraday
{% endapi-method-summary %}

{% api-method-description %}
상품/지수선물 종목 10초/분별 데이터 제공
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
업종코드 ex\) K1
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(3\) | 업종코드 | 0 |
| isuNm | String\(80\) | 종목명 |  |
| hisLists | Array\(4\) | 과거리스트 |  |
| inddTm | string\(8\) | 일중시간 | HH:MM:SS |
| inddOpnprc | number\(11\) | 일중시가 | 일중데이타\(10초, 1분, 10분\) |
| inddHgprc | number\(11\) | 일중고가 | 일중데이타\(10초, 1분, 10분\) |
| inddLwprc | number\(11\) | 일중저가 | 일중데이타\(10초, 1분, 10분\) |
| inddClsprc | number\(11\) | 일중종가 | 일중데이타\(10초, 1분, 10분\) |
| inddTrdvol | number\(11\) | 일중거래량 | 일중데이타\(10초, 1분, 10분\) |





## 업종 히스토리

{% api-method method="get" host="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/history" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/history
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
업종코드 ex\) K1
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

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(3\) | 업종코드 | 코드표 &gt;업종코드표 참조 |
| isuKorNm | String\(80\) | 종목한글명 |  |
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



