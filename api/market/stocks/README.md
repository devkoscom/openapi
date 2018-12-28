# 주식 시세

주식시장\(유가증권, 코스닥\) 의 종목 리스트, 종목 마스터, 종목 체결, 호가잔량, 종목 투자자별 종가등을 제공한다.

## Syntax

HTTP methods \| **GET**

Authentication \| **API Key**

## 주식종목 리스트 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/lists" %}
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

### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| trdDd | String\(8\) | 체결일자, 거래일자, 매매일자 | YYYYMMDD |
| isuLists | Array\(4\) | 종목리스트 | 데이터 개수 |
| isuCd | String\(12\) | 종목코드 |  |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuKorNm | String\(80\) | 종목한글명 |  |
| isuKorAbbrv | String\(40\) | 종목한글약명 | 가나다 |

### Request Example  <a id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/lists'
```

### Response Example

```yaml
{
   "trdDd": "20181228",
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

    {
       "isuSrtCd": "000040",
       "isuCd": "KR7000040006",
       "isuKorNm": "KR모터스",
       "isuKorAbbr": "KR모터스",
       "map_to": "000040*001" 
    },
    .
    .
    .
    {
       "isuSrtCd": "900140",
       "isuCd": "KYG5307W1015",
       "isuKorNm": "엘브이엠씨홀딩스",
       "isuKorAbbr": "엘브이엠씨홀딩스",
       "map_to": "900140*001" 
    } 
  ] 
}
```

## 주식종목 마스터 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/master" %}
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

### Response Parameters

| **Name** | **Type** | **Description** | ​ |
| :--- | :--- | :--- | :--- |
| trdDd | string\(8\) | 체결일자, 거래일자, 매매일자 | YYYYMMDD |
| isuCd | string\(12\) | 종목코드 | ​ |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| isuKorAbbrv | string\(40\) | 종목한글약명 | 가나다 |
| secugrpId | string\(2\) | 증권그룹ID | ST:주권, MF:증권투자회사, RT:부동산투자회사, SC:선박투자회사,IF:사회간접자본투융자회사, DR:주식예탁증서, EW:ELW, EF:ETF,SW:신주인수권증권, SR:신주인수권증서, BC:수익증권, FE:해외ETF, FS:외국주권, EN:ETN |
| mktWarnTpCd | string\(2\) | 시장경보구분코드 | 00:해당없음\(시장경보가 지정될 수 있는 종목에 대해서 지정된 바가 없음을 의미\), 01:투자주의, 02:투자경고, 03:투자위험 |
| admisuYn | string\(1\) | 관리종목여부 | Y:관리 N:일반 |
| haltYn | string\(1\) | 거래정지여부 | Y, N |
| idxIndMidclssCd | string\(3\) | 지수업종중분류코드 | 업종분류, 상세코드는 코드표\(업종\) 참고 |
|  |  |  |  |
| mktcapScaleCd | string\(1\) | 시가총액규모코드 | 유가 \(0:제외 1:대 2:중 3:소\) / 코스닥 \(0:제외 1:KOSDAQ100 2:KOSDAQmid300 3:KOSDAQsmall\) |
|  |  |  |  |
| mfindYn | string\(1\) | 제조업여부 | Y, N \(유가\)제조업여부 |
| smeYn | string\(1\) | 중소기업여부 | Y, N \(코스닥\)중소기업여부 |
| 업종 | string\(1\) | KRX100종목여부 | Y, N |
| kospiYn | string\(1\) | KOSPI여부 | Y,N \(유가\)KOSPI100여부 \(코스닥\)프리미어여부 |
| kospi100Yn | string\(1\) | KOSPI100여부 | Y, N \(유가\)KOSPI여부 |
| kospi50Yn | string\(1\) | KOSPI50여부 | Y, N \(유가\)KOSPI50여부 |
| basPrc | number\(11\) | 기준가격,기준가액 |  |
| prevddClsprc | number\(11\) | 전일종가 |  |
| prevddAccTrdvol | number\(12\) | 상장중최저가일자 |  |
| prevddAccTrdval | number\(22\) | 전일누적거래대금 |  |
| uplmtprc | number\(11\) | 상한가 |  |
| lwlmtprc | number\(11\) | 하한가 |  |
| sbPrc | number\(11\) | 대용가격 | ST,FS,DR,MF,RT,SC,IF,ET,FE,BC,EN 만 해당 |
| parval | number\(11\) | 액면가 | 외국주권일 경우 소숫점셋째자리까지 표현가능/코스닥의 각국의 최소화폐단위 표시는 유가기준으로 통일 ※ST,FS,RT,SC,BC만 해당 |
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

### Request Example  <a id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/lists'
```

### Response Example

```yaml
{
   "trdDd": "20181228",
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

    {
       "isuSrtCd": "000040",
       "isuCd": "KR7000040006",
       "isuKorNm": "KR모터스",
       "isuKorAbbr": "KR모터스",
       "map_to": "000040*001" 
    },
    .
    .
    .
    {
       "isuSrtCd": "900140",
       "isuCd": "KYG5307W1015",
       "isuKorNm": "엘브이엠씨홀딩스",
       "isuKorAbbr": "엘브이엠씨홀딩스",
       "map_to": "900140*001" 
    } 
  ] 
}
```

## 주식종목 종가 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/closeprice" %}
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

```text
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | String\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 |  |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |

### Request Example  <a id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/closeprice'
```

### Response Example

```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```

## 주식종목 체결 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/price" %}
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

```text
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | string\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
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
| bidordPrc\_1 | number\(11\) | 매수호가가격\_1 | 단위:원 |

> `trdTm`  
> HHMMSSmm 형태로 시간전송
>
> * 정규장 개시전 또는 정규장 체결 발생 이전 : 0  
> * 장운영시그널, 대량체결 포함  
>
>   ※ _장운영시그널_  
>
>   정규장마감\(15:00\):31000000 /장종료시간외마감\(15:30\):41000000 /단일가마감\(18:00\):81000000 /일반Buy-in마감\(18:00\):91000007 /당일Buy-in마감\(18:00\):91000008  
>
>   ※ _대량체결시_   
>
>   장전대량매매체결:51000000 /장중대량매매체결:61000000 /장후대량매매체결:71000000

### Request Example  <a id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/price'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "005930",
     "trdPrc": 38600,
     "cmpprevddTpCd": "2",
     "opnprc": 38250,
     "hgprc": 38900,
     "lwprc": 38200,
     "accTrdvol": 2829006,
     "trdTm": 9544500,
     "trdvol": 76,
     "accTrdval": 108981501200,
     "cmpprevddPrc": 350,
     "bidordPrc_1": 38600,
     "askordPrc_1": 38650,
     "lstAskbidTpCd": 1 
  } 
}
```

## 주식종목 호가잔량 API  <a id="api"></a>

**LP호가 제외**

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/orderbook" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/orderbook
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
     "askStep1BstordPrc": 49550,
     "askStep2BstordPrc": 49600,
     "askStep3BstordPrc": 49650,
     "askStep4BstordPrc": 49700,
     "askStep5BstordPrc": 49750,
     "askStep6BstordPrc": 49800,
     "askStep7BstordPrc": 49850,
     "askStep8BstordPrc": 49900,
     "askStep9BstordPrc": 49950,
     "askStep10BstordPrc": 50000,
     "askStep1BstordRqty": 8540,
     "askStep2BstordRqty": 50070,
     "askStep3BstordRqty": 51234,
     "askStep4BstordRqty": 50025,
     "askStep5BstordRqty": 68761,
     "askStep6BstordRqty": 69198,
     "askStep7BstordRqty": 19611,
     "askStep8BstordRqty": 58397,
     "askStep9BstordRqty": 38738,
     "askStep10BstordRqty": 33875,
     "bidStep1BstordPrc": 49500,
     "bidStep2BstordPrc": 49450,
     "bidStep3BstordPrc": 49400,
     "bidStep4BstordPrc": 49350,
     "bidStep5BstordPrc": 49300,
     "bidStep6BstordPrc": 49250,
     "bidStep7BstordPrc": 49200,
     "bidStep8BstordPrc": 49150,
     "bidStep9BstordPrc": 49100,
     "bidStep10BstordPrc": 49050,
     "bidStep1BstordRqty": 416587,
     "bidStep2BstordRqty": 103798,
     "bidStep3BstordRqty": 111538,
     "bidStep4BstordRqty": 35168,
     "bidStep5BstordRqty": 69624,
     "bidStep6BstordRqty": 32293,
     "bidStep7BstordRqty": 100011,
     "bidStep8BstordRqty": 53010,
     "bidStep9BstordRqty": 124551,
     "bidStep10BstordRqty": 61867,
     "askordTotRqty": 448449,
     "bidordTotRqty": 1108447,
     "pstoffhrAskTotOrdRqty": 0,
     "pstoffhrBidTotOrdRqty": 91373,
     "accTrdvol": 20498098,
     "deemTrdPrc": 49500,
     "deemTrdvol": 0,
     "deemAccTrdvol": 1650992 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 -&gt; 000660 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위: 주 |
| askStep1BstordPrc | number\(11\) | 매도1단계우선호가가격 |  |
| bidStep1BstordPrc | number\(11\) | 매수1단계우선호가가격 |  |
| askStep1BstordRqty | number\(12\) | 매도1단계우선호가잔량 |  |
| bidStep1BstordRqty | number\(12\) | 매수1단계우선호가잔량 |  |
| askStep2BstordPrc | number\(11\) | 매도2단계우선호가가격 |  |
| bidStep2BstordPrc | number\(11\) | 매수2단계우선호가가격 |  |
| askStep2BstordRqty | number\(12\) | 매도2단계우선호가잔량 |  |
| bidStep2BstordRqty | number\(12\) | 매수2단계우선호가잔량 |  |
| askStep3BstordPrc | number\(11\) | 매도3단계우선호가가격 |  |
| bidStep3BstordPrc | number\(11\) | 매수3단계우선호가가격 |  |
| askStep3BstordRqty | number\(12\) | 매도3단계우선호가잔량 |  |
| bidStep3BstordRqty | number\(12\) | 매수3단계우선호가잔량 |  |
| askStep4BstordPrc | number\(11\) | 매도4단계우선호가가격 |  |
| bidStep4BstordPrc | number\(11\) | 매수4단계우선호가가격 |  |
| askStep4BstordRqty | number\(12\) | 매도4단계우선호가잔량 |  |
| bidStep4BstordRqty | number\(12\) | 매수4단계우선호가잔량 |  |
| askStep5BstordPrc | number\(11\) | 매도5단계우선호가가격 |  |
| bidStep5BstordPrc | number\(11\) | 매수5단계우선호가가격 |  |
| askStep5BstordRqty | number\(12\) | 매도5단계우선호가잔량 |  |
| bidStep5BstordRqty | number\(12\) | 매수5단계우선호가잔량 |  |
| askStep6BstordPrc | number\(11\) | 매도6단계우선호가가격 |  |
| bidStep6BstordPrc | number\(11\) | 매수6단계우선호가가격 |  |
| askStep6BstordRqty | number\(12\) | 매도6단계우선호가잔량 |  |
| bidStep6BstordRqty | number\(12\) | 매수6단계우선호가잔량 |  |
| askStep7BstordPrc | number\(11\) | 매도7단계우선호가가격 |  |
| bidStep7BstordPrc | number\(11\) | 매수7단계우선호가가격 |  |
| askStep7BstordRqty | number\(12\) | 매도7단계우선호가잔량 |  |
| bidStep7BstordRqty | number\(12\) | 매수7단계우선호가잔량 |  |
| askStep8BstordPrc | number\(11\) | 매도8단계우선호가가격 |  |
| bidStep8BstordPrc | number\(11\) | 매수8단계우선호가가격 |  |
| askStep8BstordRqty | number\(12\) | 매도8단계우선호가잔량 |  |
| bidStep8BstordRqty | number\(12\) | 매수8단계우선호가잔량 |  |
| askStep9BstordPrc | number\(11\) | 매도9단계우선호가가격 |  |
| bidStep9BstordPrc | number\(11\) | 매수9단계우선호가가격 |  |
| askStep9BstordRqty | number\(12\) | 매도9단계우선호가잔량 |  |
| bidStep9BstordRqty | number\(12\) | 매수9단계우선호가잔량 |  |
| askStep10BstordPrc | number\(11\) | 매도10단계우선호가가격 |  |
| bidStep10BstordPrc | number\(11\) | 매수10단계우선호가가격 |  |
| askStep10BstordRqty | number\(12\) | 매도10단계우선호가잔량 |  |
| bidStep10BstordRqty | number\(12\) | 매수10단계우선호가잔량 |  |
| askordTotRqty | number\(12\) | 매도호가총잔량 |  |
| bidordTotRqty | number\(12\) | 매수호가총잔량 |  |
| pstoffhrAskTotOrdRqty | number\(15\) | 장종료후시간외매도총호가잔량 |  |
| pstoffhrBidTotOrdRqty | number\(15\) | 장종료후시간외매수총호가잔량 |  |
| deemTrdPrc | number\(11\) | 예상체결가격 |  |
| deemTrdvol | number\(12\) | 예상체결수량 |  |
| deemAccTrdvol | number\(12\) | 예상누적체결수량 |  |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/orderbook'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "005930",
     "askStep1BstordPrc": 38600,
     "askStep2BstordPrc": 38650,
     "askStep3BstordPrc": 38700,
     "askStep4BstordPrc": 38750,
     "askStep5BstordPrc": 38800,
     "askStep6BstordPrc": 38850,
     "askStep7BstordPrc": 38900,
     "askStep8BstordPrc": 38950,
     "askStep9BstordPrc": 39000,
     "askStep10BstordPrc": 39050,
     "askStep1BstordRqty": 3901,
     "askStep2BstordRqty": 28867,
     "askStep3BstordRqty": 24498,
     "askStep4BstordRqty": 24882,
     "askStep5BstordRqty": 57983,
     "askStep6BstordRqty": 71840,
     "askStep7BstordRqty": 94161,
     "askStep8BstordRqty": 67534,
     "askStep9BstordRqty": 94561,
     "askStep10BstordRqty": 18525,
     "bidStep1BstordPrc": 38550,
     "bidStep2BstordPrc": 38500,
     "bidStep3BstordPrc": 38450,
     "bidStep4BstordPrc": 38400,
     "bidStep5BstordPrc": 38350,
     "bidStep6BstordPrc": 38300,
     "bidStep7BstordPrc": 38250,
     "bidStep8BstordPrc": 38200,
     "bidStep9BstordPrc": 38150,
     "bidStep10BstordPrc": 38100,
     "bidStep1BstordRqty": 36810,
     "bidStep2BstordRqty": 31051,
     "bidStep3BstordRqty": 28211,
     "bidStep4BstordRqty": 22147,
     "bidStep5BstordRqty": 24657,
     "bidStep6BstordRqty": 40018,
     "bidStep7BstordRqty": 38243,
     "bidStep8BstordRqty": 27741,
     "bidStep9BstordRqty": 22552,
     "bidStep10BstordRqty": 31296,
     "askordTotRqty": 486752,
     "bidordTotRqty": 302726,
     "pstoffhrAskTotOrdRqty": 0,
     "pstoffhrBidTotOrdRqty": 0,
     "accTrdvol": 2968951,
     "deemTrdPrc": 0,
     "deemTrdvol": 0,
     "deemAccTrdvol": 0 
  } 
}
```

## 주식종목별 투자자별 종가 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/investors" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/investors
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
     "isuCd": "KR7005930003",
     "isuSrtCd": "005930",
     "invstLists": [ 
      {
         "invstCd": "01",
         "askTrdvol": 2624215,
         "askTrdval": 131761498,
         "bidTrdvol": 549821,
         "bidTrdval": 27510307 
      },
      {
         "invstCd": "02",
         "askTrdvol": 344289,
         "askTrdval": 17107455,
         "bidTrdvol": 434960,
         "bidTrdval": 21726525 
      },
       ...이하 생략...
      {
         "invstCd": "16",
         "askTrdvol": 82305,
         "askTrdval": 4139264,
         "bidTrdvol": 133696,
         "bidTrdval": 6688786 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameters**

| **Name** | **Type** | **Description** |
| :--- | :--- | :--- |
| isuSrtCd | string\(9\) | 종목단축코드 |
| invstLists | Array\(4\) | 투자자리스트 |
| invstCd | string\(4\) | 투자자코드 \(참조 :투자자코드표'\) |
| askTrdvol | number\(10\) | 매도체결수량,매도거래량 |
| askTrdval | number\(22\) | 매도거래대금 |
| bidTrdvol | number\(10\) | 매수체결수량,매수거래량 |
| bidTrdval | number\(22\) | 매수거래대금 |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/investors'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuCd": "KR7005930003",
     "isuSrtCd": "005930",
     "invstLists": [ 
      {
         "invstCd": "01",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "02",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "03",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "04",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "05",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "06",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "07",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "08",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "09",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "10",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "11",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "12",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "13",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "14",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "15",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "16",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      } 
    ] 
  } 
}
```

## KOSPI/KOSDAQ 지수 투자자 마감정보 API

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/investors" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/investors
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
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
   "jsonrpc": "2.0",
   "result": 
  {
     "Tm": "0",
     "isuSrtCd": "K1",
     "invstLists": [ 
      {
         "invstCd": "0",
         "askTrdvol": 6036208,
         "askTrdval": 199945230,
         "bidTrdvol": 6123967,
         "bidTrdval": 245146511 
      },
       ...이하 생략...
      {
         "invstCd": "0",
         "askTrdvol": 6816483,
         "askTrdval": 41879010,
         "bidTrdvol": 6145938,
         "bidTrdval": 77914532 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameters**

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| Tm | string\(8\) | 장시간 | HHMMSSmm |
| invstLists | Array\(4\) | 투자자리스트 |  |
| invstCd | string\(4\) | 투자자코드 | '투자자코드표' 참조 |
| askTrdvol | number\(10\) | 매도체결수량,매도거래량 |  |
| askTrdval | number\(22\) | 매도거래대금 |  |
| bidTrdvol | number\(10\) | 매수체결수량,매수거래량 |  |
| bidTrdval | number\(22\) | 매수거래대금 |  |

### Request Example  <a id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/investors'
```

### Response Example

```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```

## KOSPI/KOSDAQ 지수 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/index" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/index
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
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
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameters**

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | String\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
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

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/index'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "isuCnt": 901,
     "trdPrc": 2041.71,
     "cmpprevddTpCd": "2",
     "opnprc": 2036.7,
     "hgprc": 2044.03,
     "lwprc": 2035.41,
     "accTrdvol": 100875,
     "accTrdval": 948554,
     "mktcap": 1343984726,
     "cmpprevddPrc": 13.27,
     "listShrs": 55522062 
  } 
}
```

## 주식 거래 상위 회원사 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/traderanking" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/traderanking
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
     "isuSrtCd": "005930*001",
     "askTrdVolMbr1": 1624492,
     "askTrdVolMbr2": 1513371,
     "askTrdVolMbr3": 1375482,
     "askTrdVolMbr4": 1329901,
     "askTrdVolMbr5": 1047098,
     "askTrdAmtMbr1": 81468964800,
     "askTrdAmtMbr2": 75912353450,
     "askTrdAmtMbr3": 68980967250,
     "askTrdAmtMbr4": 66647026950,
     "askTrdAmtMbr5": 52154008800,
     "askTrdWtMbr1": 8.05,
     "askTrdWtMbr2": 7.5,
     "askTrdWtMbr3": 6.82,
     "askTrdWtMbr4": 6.59,
     "askTrdWtMbr5": 5.19,
     "bidTrdVolMbr1": 2173655,
     "bidTrdVolMbr2": 2040900,
     "bidTrdVolMbr3": 1615481,
     "bidTrdVolMbr4": 1602244,
     "bidTrdVolMbr5": 1426981,
     "bidTrdAmtMbr1": 108687418100,
     "bidTrdAmtMbr2": 102074693350,
     "bidTrdAmtMbr3": 80907780450,
     "bidTrdAmtMbr4": 80022847600,
     "bidTrdAmtMbr5": 71408978100,
     "bidTrdWtMbr1": 10.78,
     "bidTrdWtMbr2": 10.12,
     "bidTrdWtMbr3": 8.01,
     "bidTrdWtMbr4": 7.94,
     "bidTrdWtMbr5": 7.07,
     "bidTrdPrcMbr1": 50002,
     "bidTrdPrcMbr2": 50015,
     "bidTrdPrcMbr3": 50083,
     "bidTrdPrcMbr4": 49944,
     "bidTrdPrcMbr5": 50042,
     "askTrdPrcMbr1": 50150,
     "askTrdPrcMbr2": 50161,
     "askTrdPrcMbr3": 50150,
     "askTrdPrcMbr4": 50114,
     "askTrdPrcMbr5": 49808,
     "bidTrdMbr1": "키움증권",
     "bidTrdMbr2": "미래에셋대우",
     "bidTrdMbr3": "신한투자",
     "bidTrdMbr4": "삼성증권",
     "bidTrdMbr5": "NH투자증권",
     "askTrdMbr1": "미래에셋대우",
     "askTrdMbr2": "CS",
     "askTrdMbr3": "HSBC증권",
     "askTrdMbr4": "모간스탠리",
     "askTrdMbr5": "삼성증권" 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameters**

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| bidTrdMbr1 | string\(64\) | 매수상위회원명1 | 매수랭킹 TOP5 1위 회원사 한글명 |
| bidTrdMbr2 | string\(64\) | 매수상위회원명2 | 매수랭킹 TOP5 2위 회원사 한글명 |
| bidTrdMbr3 | string\(64\) | 매수상위회원명3 | 매수랭킹 TOP5 3위 회원사 한글명 |
| bidTrdMbr4 | string\(64\) | 매수상위회원명4 | 매수랭킹 TOP5 4위 회원사 한글명 |
| bidTrdMbr5 | string\(64\) | 매수상위회원명5 | 매수랭킹 TOP5 5위 회원사 한글명 |
| askTrdMbr1 | string\(64\) | 매도상위회원명1 | 매도랭킹 TOP5 1위 회원사 한글명 |
| askTrdMbr2 | string\(64\) | 매도상위회원명2 | 매도랭킹 TOP5 2위 회원사 한글명 |
| askTrdMbr3 | string\(64\) | 매도상위회원명3 | 매도랭킹 TOP5 3위 회원사 한글명 |
| askTrdMbr4 | string\(64\) | 매도상위회원명4 | 매도랭킹 TOP5 4위 회원사 한글명 |
| askTrdMbr5 | string\(64\) | 매도상위회원명5 | 매도랭킹 TOP5 5위 회원사 한글명 |
| bidTrdVolMbr1 | number\(11\) | 매수상위거래량 회원1 | 매수랭킹 TOP5 1위 회원사 거래량 |
| bidTrdVolMbr2 | number\(11\) | 매수상위거래량 회원2 |  |
| bidTrdVolMbr3 | number\(11\) | 매수상위거래량 회원3 |  |
| bidTrdVolMbr4 | number\(11\) | 매수상위거래량 회원4 |  |
| bidTrdVolMbr5 | number\(11\) | 매수상위거래량 회원5 |  |
| askTrdVolMbr1 | number\(11\) | 매도상위거래량 회원1 | 매도랭킹 TOP5 1위 회원사 거래량 |
| askTrdVolMbr2 | number\(11\) | 매도상위거래량 회원2 |  |
| askTrdVolMbr3 | number\(11\) | 매도상위거래량 회원3 |  |
| askTrdVolMbr4 | number\(11\) | 매도상위거래량 회원4 |  |
| askTrdVolMbr5 | number\(11\) | 매도상위거래량 회원5 |  |
| bidTrdAmtMbr1 | number\(11\) | 매수상위거래금액 회원1 | 매수랭킹 TOP5 1위 회원사 거래금액 |
| bidTrdAmtMbr2 | number\(11\) | 매수상위거래금액 회원2 |  |
| bidTrdAmtMbr3 | number\(11\) | 매수상위거래금액 회원3 |  |
| bidTrdAmtMbr4 | number\(11\) | 매수상위거래금액 회원4 |  |
| bidTrdAmtMbr5 | number\(11\) | 매수상위거래금액 회원5 |  |
| askTrdAmtMbr1 | number\(11\) | 매도상위거래금액 회원1 | 매도랭킹 TOP5 1위 회원사 거래금액 |
| askTrdAmtMbr2 | number\(11\) | 매도상위거래금액 회원2 |  |
| askTrdAmtMbr3 | number\(11\) | 매도상위거래금액 회원3 |  |
| askTrdAmtMbr4 | number\(11\) | 매도상위거래금액 회원4 |  |
| askTrdAmtMbr5 | number\(11\) | 매도상위거래금액 회원5 |  |
| bidTrdPrcMbr1 | number\(11\) | 매수상위거래단가 회원1 | 매수랭킹 TOP5 1위 회원사 거래단가 |
| bidTrdPrcMbr2 | number\(11\) | 매수상위거래단가 회원2 |  |
| bidTrdPrcMbr3 | number\(11\) | 매수상위거래단가 회원3 |  |
| bidTrdPrcMbr4 | number\(11\) | 매수상위거래단가 회원4 |  |
| bidTrdPrcMbr5 | number\(11\) | 매수상위거래단가 회원5 |  |
| askTrdPrcMbr1 | number\(11\) | 매도상위거래단가 회원1 | 매도랭킹 TOP5 1위 회원사 거래단가 |
| askTrdPrcMbr2 | number\(11\) | 매도상위거래단가 회원2 |  |
| askTrdPrcMbr3 | number\(11\) | 매도상위거래단가 회원3 |  |
| askTrdPrcMbr4 | number\(11\) | 매도상위거래단가 회원4 |  |
| askTrdPrcMbr5 | number\(11\) | 매도상위거래단가 회원5 |  |
| bidTrdWtMbr1 | number\(5\) | 매수상위거래비중 회원1 | 매수랭킹 TOP5 1위 회원사 거래비중 \(백분율, X100\) |
| bidTrdWtMbr2 | number\(5\) | 매수상위거래비중 회원2 |  |
| bidTrdWtMbr3 | number\(5\) | 매수상위거래비중 회원3 |  |
| bidTrdWtMbr4 | number\(5\) | 매수상위거래비중 회원4 |  |
| bidTrdWtMbr5 | number\(5\) | 매수상위거래비중 회원5 |  |
| askTrdWtMbr1 | number\(5\) | 매도상위거래비중 회원1 | 매도랭킹 TOP5 1위 회원사 거래비중 \(백분율, X100\) |
| askTrdWtMbr2 | number\(5\) | 매도상위거래비중 회원2 |  |
| askTrdWtMbr3 | number\(5\) | 매도상위거래비중 회원3 |  |
| askTrdWtMbr4 | number\(5\) | 매도상위거래비중 회원4 |  |
| askTrdWtMbr5 | number\(5\) | 매도상위거래비중 회원5 |  |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/traderanking'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "005930*001",
     "askTrdVolMbr1": 337141,
     "askTrdVolMbr2": 301678,
     "askTrdVolMbr3": 263659,
     "askTrdVolMbr4": 225961,
     "askTrdVolMbr5": 201467,
     "askTrdAmtMbr1": 12987257800,
     "askTrdAmtMbr2": 11586362850,
     "askTrdAmtMbr3": 10181206900,
     "askTrdAmtMbr4": 8707360050,
     "askTrdAmtMbr5": 7756513450,
     "askTrdWtMbr1": 11.62,
     "askTrdWtMbr2": 10.4,
     "askTrdWtMbr3": 9.09,
     "askTrdWtMbr4": 7.79,
     "askTrdWtMbr5": 6.94,
     "bidTrdVolMbr1": 692835,
     "bidTrdVolMbr2": 333573,
     "bidTrdVolMbr3": 173089,
     "bidTrdVolMbr4": 165312,
     "bidTrdVolMbr5": 160117,
     "bidTrdAmtMbr1": 26663102100,
     "bidTrdAmtMbr2": 12877911700,
     "bidTrdAmtMbr3": 6655224300,
     "bidTrdAmtMbr4": 6375021600,
     "bidTrdAmtMbr5": 6167793600,
     "bidTrdWtMbr1": 23.88,
     "bidTrdWtMbr2": 11.5,
     "bidTrdWtMbr3": 5.97,
     "bidTrdWtMbr4": 5.7,
     "bidTrdWtMbr5": 5.52,
     "bidTrdPrcMbr1": 38484,
     "bidTrdPrcMbr2": 38606,
     "bidTrdPrcMbr3": 38450,
     "bidTrdPrcMbr4": 38564,
     "bidTrdPrcMbr5": 38521,
     "askTrdPrcMbr1": 38522,
     "askTrdPrcMbr2": 38406,
     "askTrdPrcMbr3": 38615,
     "askTrdPrcMbr4": 38535,
     "askTrdPrcMbr5": 38500,
     "bidTrdMbr1": "CLSA",
     "bidTrdMbr2": "하이증권",
     "bidTrdMbr3": "맥쿼리",
     "bidTrdMbr4": "미래에셋대우",
     "bidTrdMbr5": "키움증권",
     "askTrdMbr1": "하이증권",
     "askTrdMbr2": "CS",
     "askTrdMbr3": "키움증권",
     "askTrdMbr4": "미래에셋대우",
     "askTrdMbr5": "메릴린치" 
  } 
}
```

## 주식종목\(ETF\) 장마감후 순자산가치 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/closenav" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/closenav
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
     "isuSrtCd": "590003",
     "nav": 11936.79,
     "cmpprevddNav": -156.52 
  } 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```text
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameters**

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| nav | number\(11\) | 순자산가치 |  |
| cmpprevddNav | number\(11\) | 전일대비순자산가치 |  |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/closenav'
```

### Response Example

```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```

## 주식 공매도 API  <a id="api"></a>

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/shortsell" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/shortsell
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

{% api-method-query-parameters %}
{% api-method-parameter type="string" name="inqStrtDd" required=false %}
조회시작일자
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqEndDd" required=true %}
조회종료일자
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
     "isuSrtCd": "005930",
     "hisLists": [ 
      {
         "BzDd": 20180102,
         "lendBalQty": 0,
         "lendBalAmt": 0,
         "srtsellTrdVol": 1266,
         "srtsellTrdAmt": 3229159000 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

**Response Parameter**

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| hisLists | Array\(4\) | 과거리스트 |  |
| trdDd | string\(8\) | 체결일자,거래일자,매매일자 | YYYYMMDD |
| srtsellTrdvol | number\(11\) | 공매도거래량 | 공매도거래량\(주식수, 전일기준\) |
| srtsellTrdAmt | number\(11\) | 공매도거래금액 | 공매도거래금액\(주식수, 전일기준\) |
| lendBalQty | number\(11\) | 대차잔고수량 | 대차잔고수량\(주식수, 전일기준\) |
| lendBalAmt | number\(11\) | 대차잔고금액 | 단위 1,000 원 |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/shortsell?inqStrtDd=20181001&inqEndDd=20181231'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "005930",
     "hisLists": [ 
      {
         "BzDd": 20181228,
         "lendBalQty": 0,
         "lendBalAmt": 0,
         "srtsellTrdVol": 0,
         "srtsellTrdAmt": 0 
      },

      {
         "BzDd": 20181227,
         "lendBalQty": 96176577,
         "lendBalAmt": 3678754070,
         "srtsellTrdVol": 0,
         "srtsellTrdAmt": 0 
      },

      {
         "BzDd": 20181226,
         "lendBalQty": 100432709,
         "lendBalAmt": 3851594390,
         "srtsellTrdVol": 0,
         "srtsellTrdAmt": 0 
      },
      .
      .
      .

      {
         "BzDd": 20181019,
         "lendBalQty": 98588612,
         "lendBalAmt": 4328040067,
         "srtsellTrdVol": 718889,
         "srtsellTrdAmt": 31521849500 
      } 
    ] 
  } 
}
```

## 주식 종목 일중 API

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/intraday" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/intraday
{% endapi-method-summary %}

{% api-method-description %}
최대 100건 까지만 조회 가능
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분
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
개시시각,시작시각 \(HHMM\)
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

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(9\) | 종목단축코드 |  |
| isuNm | String\(80\) | 종목명 |  |
| hisLists | Array\(4\) | 과거리스트 |  |
| inddTm | string\(8\) | 일중시간 | HH:MM:SS |
| inddOpnprc | number\(11\) | 일중시가 | 일중데이타\(10초, 1분, 10분\) |
| inddHgprc | number\(11\) | 일중고가 | 일중데이타\(10초, 1분, 10분\) |
| inddLwprc | number\(11\) | 일중저가 | 일중데이타\(10초, 1분, 10분\) |
| inddClsprc | number\(11\) | 일중종가 | 일중데이타\(10초, 1분, 10분\) |
| inddTrdvol | number\(11\) | 일중거래량 | 일중데이타\(10초, 1분, 10분\) |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/intraday?inddCycleTpCd=600&inqStrtDd=20181228&strtTm=0900&endTm=1500'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "005930",
     "hisLists": [ 
      {
         "inddTm": "10032000",
         "inddOpnprc": 38600,
         "inddHgprc": 38600,
         "inddLwprc": 38500,
         "inddClsprc": 38500,
         "inddTrdvol": 2929814 
      },

      {
         "inddTm": "10000000",
         "inddOpnprc": 38700,
         "inddHgprc": 38700,
         "inddLwprc": 38550,
         "inddClsprc": 38600,
         "inddTrdvol": 2903276 
      },

      {
         "inddTm": "9500000",
         "inddOpnprc": 38700,
         "inddHgprc": 38750,
         "inddLwprc": 38600,
         "inddClsprc": 38700,
         "inddTrdvol": 2778449 
      },

      {
         "inddTm": "9400000",
         "inddOpnprc": 38550,
         "inddHgprc": 38550,
         "inddLwprc": 38550,
         "inddClsprc": 38550,
         "inddTrdvol": 1695991 
      },

      {
         "inddTm": "9300000",
         "inddOpnprc": 38500,
         "inddHgprc": 38550,
         "inddLwprc": 38450,
         "inddClsprc": 38550,
         "inddTrdvol": 1695991 
      },

      {
         "inddTm": "9200000",
         "inddOpnprc": 38450,
         "inddHgprc": 38550,
         "inddLwprc": 38300,
         "inddClsprc": 38500,
         "inddTrdvol": 1275121 
      },

      {
         "inddTm": "9100000",
         "inddOpnprc": 38250,
         "inddHgprc": 38550,
         "inddLwprc": 38200,
         "inddClsprc": 38400,
         "inddTrdvol": 870273 
      } 
    ] 
  } 
}
```

## 주식 외국인보유율 히스토리 API

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/foreignhistory" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/foreignhistory
{% endapi-method-summary %}

{% api-method-description %}
최대 100건 까지만 조회 가능
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter type="string" name="inqStrtDd" required=true %}
조회시작일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqEndDd" required=true %}
조회종료일자
{% endapi-method-parameter %}

{% api-method-parameter type="number" name="reqCnt" %}
요청건수 \(최대100건\)
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
     "isuSrtCd": "005930",
     "hisLists": [ 
      {
         "FornHdVol": 68095088,
         "cmpprevddFornHdVol": 5862,
         "FornHdVolRt": 52.75,
         "BzDd": 20180102 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(9\) | 종목단축코드 |  |
| hisLists | Array\(4\) | 과거리스트 |  |
| trdDd | string\(8\) | 체결일자,거래일자,매매일자 |  |
| FornHdVol | number\(11\) | 외국인보유주식수 |  |
| cmpprevddFornHdVol | number\(11\) | 외국인보유주식수전일대비 |  |
| FornHdVolRt | number\(5\) | 외국인보유율 |  |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/foreignhistory?inqStrtDd=20181001&inqEndDd=20181231&reqCnt=20'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "005930",
     "hisLists": [ 
      {
         "FornHdVol": 3315501801,
         "cmpprevddFornHdVol": 0,
         "FornHdVolRt": 55.54,
         "BzDd": 20181228 
      },

      {
         "FornHdVol": 3315501801,
         "cmpprevddFornHdVol": 1660604,
         "FornHdVolRt": 55.54,
         "BzDd": 20181227 
      },

      {
         "FornHdVol": 3313841197,
         "cmpprevddFornHdVol": -3541075,
         "FornHdVolRt": 55.51,
         "BzDd": 20181226 
      },

      {
         "FornHdVol": 3317382272,
         "cmpprevddFornHdVol": 839880,
         "FornHdVolRt": 55.57,
         "BzDd": 20181224 
      },

      {
         "FornHdVol": 3316542392,
         "cmpprevddFornHdVol": -4665291,
         "FornHdVolRt": 55.56,
         "BzDd": 20181221 
      },

      {
         "FornHdVol": 3321207683,
         "cmpprevddFornHdVol": 390180,
         "FornHdVolRt": 0,
         "BzDd": 20181220 
      },

      {
         "FornHdVol": 3320817503,
         "cmpprevddFornHdVol": -1753613,
         "FornHdVolRt": 55.63,
         "BzDd": 20181219 
      },

      {
         "FornHdVol": 3322571116,
         "cmpprevddFornHdVol": -2855217,
         "FornHdVolRt": 55.66,
         "BzDd": 20181218 
      },

      {
         "FornHdVol": 3325426333,
         "cmpprevddFornHdVol": -58073,
         "FornHdVolRt": 55.7,
         "BzDd": 20181217 
      },

      {
         "FornHdVol": 3325484406,
         "cmpprevddFornHdVol": -1702700,
         "FornHdVolRt": 55.71,
         "BzDd": 20181214 
      },

      {
         "FornHdVol": 3327187106,
         "cmpprevddFornHdVol": 628899,
         "FornHdVolRt": 55.73,
         "BzDd": 20181213 
      },

      {
         "FornHdVol": 3326558207,
         "cmpprevddFornHdVol": -2033979,
         "FornHdVolRt": 55.72,
         "BzDd": 20181212 
      },

      {
         "FornHdVol": 3328592186,
         "cmpprevddFornHdVol": -95076,
         "FornHdVolRt": 55.76,
         "BzDd": 20181211 
      },

      {
         "FornHdVol": 3328687262,
         "cmpprevddFornHdVol": -5089822,
         "FornHdVolRt": 51.85,
         "BzDd": 20181210 
      },

      {
         "FornHdVol": 3333777084,
         "cmpprevddFornHdVol": -581731,
         "FornHdVolRt": 51.93,
         "BzDd": 20181207 
      },

      {
         "FornHdVol": 3334358815,
         "cmpprevddFornHdVol": -6202842,
         "FornHdVolRt": 51.94,
         "BzDd": 20181206 
      },

      {
         "FornHdVol": 3340561657,
         "cmpprevddFornHdVol": -5120800,
         "FornHdVolRt": 52.04,
         "BzDd": 20181205 
      },

      {
         "FornHdVol": 3345682457,
         "cmpprevddFornHdVol": -2998508,
         "FornHdVolRt": 52.12,
         "BzDd": 20181204 
      },

      {
         "FornHdVol": 3348680965,
         "cmpprevddFornHdVol": 3417910,
         "FornHdVolRt": 52.17,
         "BzDd": 20181203 
      },

      {
         "FornHdVol": 3345263055,
         "cmpprevddFornHdVol": -1853982,
         "FornHdVolRt": 52.11,
         "BzDd": 20181130 
      } 
    ] 
  } 
}
```

## 주식 종목 히스토리

{% api-method method="get" host="https://{APIGWAddr}/v2/market/stocks" path="/{marketcode}/{issuecode}/history" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/history
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter type="string" name="trnsmCycleTpCd" required=true %}
전송주기구분코드 \(D:일별, W:주별, M:월별\) 해당기간의 마지막영업일 기준시세. ex\) W:주-금요일, M:월-31일
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqStrtDd" required=true %}
조회시작일자 \(YYYYMMDD\)
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="inqEndDd" required=true %}
조회종료일자 \(YYYYMMDD\)
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
     "isuSrtCd": "005930",
     "hisLists": [ 
      {
         "BzDd": 20180102,
         "trdPrc": 50825,
         "cmpprevddTpCd": "2",
         "opnprc": 51184,
         "hgprc": 51204,
         "lwprc": 50586,
         "accTrdvol": 169485,
         "accTrdval": 432677351468,
         "cmpprevddPrc": 59 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Response Parameters

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | String\(3\) | 종목단축코드 |  |
| hisLists | Array\(4\) | 과거리스트 |  |
| trdDd | string\(8\) | 체결일자,거래일자,매매일자 | YYYYMMDD |
| trdPrc | number\(11\) | 체결가격 |  |
| cmpprevddTpCd | string\(1\) | 전일대비구분코 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서,증권의 신규 상장 당일 : 0 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e34448c982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/005930/history?trnsmCycleTpCd=D&inqStrtDd=20181001&inqEndDd=20181231&reqCnt=20'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "005930",
     "hisLists": [ 
      {
         "BzDd": 20181228,
         "trdPrc": 38600,
         "cmpprevddTpCd": "2",
         "opnprc": 38250,
         "hgprc": 38900,
         "lwprc": 38200,
         "accTrdvol": 2955868,
         "accTrdval": 113875559350,
         "cmpprevddPrc": 350 
      },

      {
         "BzDd": 20181227,
         "trdPrc": 38250,
         "cmpprevddTpCd": "5",
         "opnprc": 38700,
         "hgprc": 38800,
         "lwprc": 38100,
         "accTrdvol": 10510643,
         "accTrdval": 403520824950,
         "cmpprevddPrc": -100 
      },

      {
         "BzDd": 20181226,
         "trdPrc": 38350,
         "cmpprevddTpCd": "0",
         "opnprc": 38400,
         "hgprc": 38750,
         "lwprc": 38300,
         "accTrdvol": 12707675,
         "accTrdval": 488546395500,
         "cmpprevddPrc": -300 
      },

      {
         "BzDd": 20181224,
         "trdPrc": 27600,
         "cmpprevddTpCd": "2",
         "opnprc": 27200,
         "hgprc": 27600,
         "lwprc": 27150,
         "accTrdvol": 6571,
         "accTrdval": 179691950,
         "cmpprevddPrc": 150 
      },

      {
         "BzDd": 20181221,
         "trdPrc": 38650,
         "cmpprevddTpCd": "3",
         "opnprc": 38200,
         "hgprc": 38650,
         "lwprc": 38100,
         "accTrdvol": 14947080,
         "accTrdval": 575188706454,
         "cmpprevddPrc": 0 
      },

      {
         "BzDd": 20181220,
         "trdPrc": 38650,
         "cmpprevddTpCd": "5",
         "opnprc": 38600,
         "hgprc": 39100,
         "lwprc": 38500,
         "accTrdvol": 11937617,
         "accTrdval": 462009678419,
         "cmpprevddPrc": -450 
      },

      {
         "BzDd": 20181219,
         "trdPrc": 39100,
         "cmpprevddTpCd": "2",
         "opnprc": 38900,
         "hgprc": 39350,
         "lwprc": 38850,
         "accTrdvol": 9942037,
         "accTrdval": 388002233278,
         "cmpprevddPrc": 200 
      },

      {
         "BzDd": 20181218,
         "trdPrc": 38900,
         "cmpprevddTpCd": "5",
         "opnprc": 38300,
         "hgprc": 39200,
         "lwprc": 38300,
         "accTrdvol": 11042101,
         "accTrdval": 429736490346,
         "cmpprevddPrc": -2800 
      },

      {
         "BzDd": 20181217,
         "trdPrc": 41700,
         "cmpprevddTpCd": "0",
         "opnprc": 36400,
         "hgprc": 45000,
         "lwprc": 36400,
         "accTrdvol": 36302,
         "accTrdval": 1536781900,
         "cmpprevddPrc": 200 
      },

      {
         "BzDd": 20181214,
         "trdPrc": 38950,
         "cmpprevddTpCd": "5",
         "opnprc": 40200,
         "hgprc": 40200,
         "lwprc": 38700,
         "accTrdvol": 19671783,
         "accTrdval": 768559029290,
         "cmpprevddPrc": -1050 
      },

      {
         "BzDd": 20181213,
         "trdPrc": 40000,
         "cmpprevddTpCd": "5",
         "opnprc": 40650,
         "hgprc": 40750,
         "lwprc": 40000,
         "accTrdvol": 26254646,
         "accTrdval": 1054672523100,
         "cmpprevddPrc": -450 
      },

      {
         "BzDd": 20181212,
         "trdPrc": 40450,
         "cmpprevddTpCd": "0",
         "opnprc": 40250,
         "hgprc": 40700,
         "lwprc": 40150,
         "accTrdvol": 12024279,
         "accTrdval": 486186060392,
         "cmpprevddPrc": 200 
      },

      {
         "BzDd": 20181211,
         "trdPrc": 51000,
         "cmpprevddTpCd": "2",
         "opnprc": 44000,
         "hgprc": 51100,
         "lwprc": 41000,
         "accTrdvol": 245805,
         "accTrdval": 10778627450,
         "cmpprevddPrc": 50 
      },

      {
         "BzDd": 20181210,
         "trdPrc": 40200,
         "cmpprevddTpCd": "5",
         "opnprc": 40450,
         "hgprc": 40650,
         "lwprc": 40000,
         "accTrdvol": 14892263,
         "accTrdval": 598916715336,
         "cmpprevddPrc": -750 
      },

      {
         "BzDd": 20181207,
         "trdPrc": 40950,
         "cmpprevddTpCd": "5",
         "opnprc": 0,
         "hgprc": 74686,
         "lwprc": 40879,
         "accTrdvol": 300026,
         "accTrdval": 11132416400,
         "cmpprevddPrc": -17398 
      },

      {
         "BzDd": 20181206,
         "trdPrc": 57287,
         "cmpprevddTpCd": "0",
         "opnprc": 0,
         "hgprc": 0,
         "lwprc": 57216,
         "accTrdvol": 14251826,
         "accTrdval": 579350131900,
         "cmpprevddPrc": -9972 
      },

      {
         "BzDd": 20181205,
         "trdPrc": 58631,
         "cmpprevddTpCd": "0",
         "opnprc": 0,
         "hgprc": 0,
         "lwprc": 0,
         "accTrdvol": 12631983,
         "accTrdval": 522454917535,
         "cmpprevddPrc": -1060 
      },

      {
         "BzDd": 20181204,
         "trdPrc": 59621,
         "cmpprevddTpCd": "5",
         "opnprc": 60328,
         "hgprc": 60682,
         "lwprc": 59267,
         "accTrdvol": 14347746,
         "accTrdval": 605987183391,
         "cmpprevddPrc": -6718 
      },

      {
         "BzDd": 20181203,
         "trdPrc": 61177,
         "cmpprevddTpCd": "2",
         "opnprc": 60470,
         "hgprc": 61389,
         "lwprc": 59975,
         "accTrdvol": 12110702,
         "accTrdval": 521013724675,
         "cmpprevddPrc": -9547 
      },

      {
         "BzDd": 20181130,
         "trdPrc": 70725,
         "cmpprevddTpCd": "5",
         "opnprc": 0,
         "hgprc": 0,
         "lwprc": 70555,
         "accTrdvol": 19775519,
         "accTrdval": 838775278782,
         "cmpprevddPrc": -2449 
      } 
    ] 
  } 
}
```

