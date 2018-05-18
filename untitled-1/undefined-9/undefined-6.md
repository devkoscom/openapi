# 주식 시세조회

주식시장\(유가증권, 코스닥\) 의 종목 리스트, 종목 마스터, 종목 체결, 호가잔량, 종목 투자자별 종가등을 제공한다.



## Syntax

HTTP methods    \|   **GET**

Authentication     \|   **API Key**





## 주식종목 리스트 API {#api}

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/stocks" path="/{marketcode}/lists" %}
{% api-method-summary %}
 /v2/market/stocks/{marketcode}/lists
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" required=true name="marketcode" %}
시장구분 \(kospi \| kosdaq\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "trdDd": "20180306",
   "mktEndTm": "1540",
   "isuLists": [ 
    {
       "isuSrtCd": "000020",
       "isuCd": "KR7000020008",
       "isuKorNm": "동화약품",
       "isuKorAbbr": "동화약품",
       "map_to": "000020*001" 
    },
     
    {
       "isuSrtCd": "000030",
       "isuCd": "KR7000030007",
       "isuKorNm": "우리은행",
       "isuKorAbbr": "우리은행",
       "map_to": "000030*001" 
    },
     ... 이하생략...
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
| isuLists | Array\(4\) | 종목리스트 | 데이터 개수 |
| isuCd | String\(12\) | 종목코드 |  |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuKorNm | String\(80\) | 종목한글명 |  |
| isuKorAbbrv | String\(40\) | 종목한글약명 | 가나다 |





## 주식종목 마스터 API {#api}

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/stocks" path="/{marketcode}/{issuecode}/master" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/master
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="marketcode" required=true type="string" %}
시장구분 \(kospi \| kosdaq\)
{% endapi-method-parameter %}

{% api-method-parameter name="issuecode" required=true type="string" %}
종목코드 ex\)005930
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
     "isuSrtCd": "005930",
     "prevddClsprc": 2650000,
     "prevddAccTrdvol": 0,
     "prevddAccTrdval": 0,
     "prevddNav": 0,
     "BzDd": 20180504,
     "acntclsMm": "12",
     "acntclsCd": "000000000001",
     "eps": 5997,
     "bps": 28126,
     "per": 8.67,
     "pbr": 1.85,
     "divYd": 0,
     "basPrc": 53000,
     "arrantrdYn": "N",
     "isuKorAbbrv": "삼성전자",
     "isuCd": "KR7005930003",
     "listDd": 19750611,
     "idxIndUpclssCd": 13,
     "idxIndMidclssCd": 13,
     "idxIndLwclssCd": 13,
     "mfindYn": "Y",
     "kospi100Yn": "N",
     "kospi50Yn": "N",
     "parval": 100,
     "dps": 850,
     "admisuYn": "N",
     "mktWarnTpCd": "00",
     "haltYn": "N",
     "isuPrc": 0,
     "uplmtprc": 68900,
     "lwlmtprc": 37100,
     "sbPrc": 41340,
     "listShrs": 6419324700,
     "regulssQtyUnit": 1,
     "mktcapScaleCd": 2,
     "kospiYn": "N",
     "invstcautnRemndIsuYn": "N",
     "srttrmOverheatIsuTpCd": "0",
     "secugrpId": "ST",
     "smeYn": "N",
     "isuTrdvol": "Y",
     "creditOrdPosblYn": "N",
     "adjStkprcCalcYn": "Y" 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Parameters

| **Name** | **Type** | **Description** | ​ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| trdDd | string\(8\) | 체결일자, 거래일자, 매매일자 | YYYYMMDD |
| isuCd | string\(12\) | 종목코드 | ​ |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuKorAbbrv | string\(40\) | 종목한글약명 | 가나다 |
| secugrpId | string\(2\) | 증권그룹ID | ST:주권, MF:증권투자회사, RT:부동산투자회사, SC:선박투자회사,IF:사회간접자본투융자회사, DR:주식예탁증서, EW:ELW, EF:ETF,SW:신주인수권증권, SR:신주인수권증서, BC:수익증권, FE:해외ETF, FS:외국주권, EN:ETN  |
| mktWarnTpCd | string\(2\) | 시장경보구분코드 | 00:해당없음\(시장경보가 지정될 수 있는 종목에 대해서 지정된 바가 없음을 의미\), 01:투자주의, 02:투자경고, 03:투자위험 |
| admisuYn | string\(1\) | 관리종목여부 | Y:관리 N:일반 |
| haltYn | string\(1\) | 거래정지여부 | Y, N  |
| idxIndMidclssCd | string\(3\) | 지수업종중분류코드 | 업종분류, 상세코드는 코드표\(업종\) 참고 |
| mktcapScaleCd | string\(1\) | 시가총액규모코드 | 유가 \(0:제외 1:대 2:중 3:소\) / 코스닥 \(0:제외 1:KOSDAQ100 2:KOSDAQmid300 3:KOSDAQsmall\) |
| mfindYn | string\(1\) | 제조업여부 | Y, N \(유가\)제조업여부 |
| smeYn | string\(1\) | 중소기업여부 | Y, N \(코스닥\)중소기업여부 |
| 업종 | string\(1\) | KRX100종목여부 | Y, N \(유가\)KOSPI100여부 \(코스닥\)프리미어여부 |
| kospiYn | string\(1\) | KOSPI여부 | Y, N |
| kospi100Yn | string\(1\) | KOSPI100여부 | Y, N \(유가\)KOSPI여부 |
| kospi50Yn | string\(1\) | KOSPI50여부 | Y, N \(유가\)KOSPI50여부 |
| basPrc | number\(11\) | 기준가격,기준가액 |  |
| prevddClsprc | number\(11\) | 전일종가 |  |
| prevddAccTrdvol | number\(12\) | 상장중최저가일자 |  |
| prevddAccTrdval | number\(22\) | 전일누적거래대금 |  |
| uplmtprc | number\(11\) | 상한가 |  |
| lwlmtprc | number\(11\) | 하한가 |  |
| sbPrc | number\(11\) | 대용가격 | ST,FS,DR,MF,RT,SC,IF,ET,FE,BC,EN 만 해당  |
| parval | number\(11\) | 액면가 | 9\(9\)V9\(3\) 외국주권일 경우 소숫점셋째자리까지 표현가능/코스닥의 각국의 최소화폐단위 표시는 유가기준으로 통일 ※ST,FS,RT,SC,BC만 해당 |
| isuPrc | number\(11\) | 발행가격 | ELW, 신주인수권증서 포함 |
| listDd | string\(8\) | 상장일자 | YYYYMMDD |
| listShrs | number\(16\) | 상장주식수,상장증권수 |  |
| arrantrdYn | string\(1\) | 정리매매여부 |  |
| creditOrdPosblYn | string\(1\) | 신용주문가능여부 | Y, N |
| regulssQtyUnit | number\(6\) | 정규장매매수량단위 |  |
| invstcautnRemndIsuYn | string\(1\) | 투자주의환기종목여부 | Y, N |
| srttrmOverheatIsuTpCd | string\(1\) | 단기과열종목구분코드 | 0: 해당없음, 1: 지정예고, 2: 지정, 3: 지정연장\(해제연기\) |
| eps | number\(11\) | 주당순이익 |  |
| per | number\(11\) | 주가수익률 |  |
| bps | number\(11\) | 주당순자산가치 |  |
| pbr | number\(11\) | 주당순자산비율 |  |
| dps | number\(11\) | 주당배당금액 |  |
| divYd | number\(11\) | 배당수익율 |  |
| acntclsCd | string\(12\) | 결산월구분 | 월별 Map 구조 \(001001001001 =&gt; 3,6,9,12 월\) |
| adjStkprcCalcYn | string\(1\) | 수정주가산출여부 | Y, N |
| prevddNav | number\(22\) | 전일순자산가치 | ETF종목일 경우 소수점 2자리로 표현, 일반종목은 0 |





## 주식종목 종가 API {#api}

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/stocks" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/closeprice
{% endapi-method-summary %}

{% api-method-description %}
종목 당일 종가제공
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분 \(kospi \| kosdaq\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드 ex\)005930
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
     "isuSrtCd": "005930",
     "trdPrc": 51900,
     "cmpprevddTpCd": "5",
     "opnprc": 53000,
     "hgprc": 53900,
     "lwprc": 51800,
     "accTrdvol": 39421505,
     "accTrdval": 2070538849200,
     "cmpprevddPrc": -1100 
  } 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
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





## 주식종목 체결 API {#api}

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/stocks" path="/{marketcode}/{issuecode}/price" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/price
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분 \(kospi \| kosdaq\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" required=true name="issuecode" %}
종목코드 ex\)005930
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
     "isuSrtCd": "005930",
     "trdPrc": 49650,
     "cmpprevddTpCd": "5",
     "opnprc": 50200,
     "hgprc": 50400,
     "lwprc": 49550,
     "accTrdvol": 4767636,
     "trdTm": 10103900,
     "trdvol": 20,
     "accTrdval": 238067176750,
     "cmpprevddPrc": -450,
     "bidordPrc_1": 49650,
     "askordPrc_1": 49700,
     "lstAskbidTpCd": 1 
  } 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
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
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | string\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 | 0 |
| trdvol | number\(10\) | 체결수량, 거래량 | 0 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |
| lstAskbidTpCd | string\(1\) | 최종매도매수구분코드 | 1:매도, 2:매수 \(최종으로 들어온 호가의 매도매수구분값\) |
| trdTm | string\(8\) | 체결시각,거래시각 | \*테이블 하단 참고 |
| askordPrc\_1 | number\(11\) | 매도호가가격\_1 | 단위:원 \(체결+우선호가 발생시에만 전송\) |
| bidordPrc\_1 | number\(11\) | 매수호가가격\_1 |  단위:원 |

> `trdTm`
>
>  "HHMMSSmm" 형태로 시간전송  
>    - 정규장 개시전 또는 정규장 체결 발생 이전 : 0  
>    - 장운영시그널, 대량체결 포함  
> ※ 장운영시그널  
>   정규장마감\(15:00\):31000000/장종료시간외마감\(15:30\):41000000/단일가마감\(18:00\):81000000/일반Buy-in마감\(18:00\):91000007/당일Buy-in마감\(18:00\):91000008  
> ※ 대량체결시 장전대량매매체결:51000000/장중대량매매체결:61000000/장후대량매매체결:71000000"



