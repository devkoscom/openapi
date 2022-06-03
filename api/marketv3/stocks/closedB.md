# 주식실시간종가B

주식시장(코스닥)의 종목 리스트, 종목 마스터 등 종가 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## KOSDAQ 주식 종목 리스트 API  <a href="#api" id="api"></a>

* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/lists" method="get" summary="/v3/market/closed/kosdaq/lists" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "mktEndTm": "1540",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "isuCd": "HK0000057197",
            "isuKorNm": "이스트아시아홀딩스",
            "isuKorAbbr": "이스트아시아홀딩스",
            "map_to": "900110*003"
        },
		...
        {
            "isuSrtCd": "900100",
            "isuCd": "USU652221081",
            "isuKorNm": "애머릿지",
            "isuKorAbbr": "애머릿지",
            "map_to": "900100*003"
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**    | **Type**   | **Description**  |                          |
| ----------- | ---------- | ---------------- | ------------------------ |
| trdDd       | String(8)  | 체결일자, 거래일자, 매매일자 | YYYYMMDD                 |
| isuLists    | Array(4)   | 종목리스트            | 데이터 개수                   |
| isuCd       | String(12) | 종목코드             |                          |
| isuSrtCd    | String(9)  | 종목단축코드           | 예) KR7000660001 → 000660 |
| isuKorNm    | String(80) | 종목한글명            |                          |
| isuKorAbbrv | String(40) | 종목한글약명           | 가나다                      |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/lists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "mktEndTm": "1540",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "isuCd": "HK0000057197",
            "isuKorNm": "이스트아시아홀딩스",
            "isuKorAbbr": "이스트아시아홀딩스",
            "map_to": "900110*003"
        },
		...
        {
            "isuSrtCd": "900100",
            "isuCd": "USU652221081",
            "isuKorNm": "애머릿지",
            "isuKorAbbr": "애머릿지",
            "map_to": "900100*003"
        }
    ]
}
```

## KOSDAQ 주식종목 마스터 API  <a href="#api" id="api"></a>

* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/{issuecode}/master" method="get" summary="/v3/market/closed/kosdaq/{issuecode}/master" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)247540
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "prevddClsprc": 505000,
        "prevddAccTrdvol": 244181,
        "prevddAccTrdval": 122258221700,
        "prevddNav": 0,
        "trdDd": 20220602,
        "acntclsMm": "12",
        "acntclsCd": "000000000001",
        "eps": 4599,
        "bps": 23807,
        "per": 109.31,
        "pbr": 21.12,
        "divYd": 0.2,
        "basPrc": 505000,
        "arrantrdYn": "N",
        "isuKorAbbrv": "에코프로비엠",
        "isuEngNm": "ECOPROBM",
        "isuCd": "KR7247540008",
        "listDd": 20190305,
        "mfindYn": "N",
        "kospi100Yn": "0",
        "kospi50Yn": " -",
        "parval": 500,
        "dps": 920,
        "admisuYn": "N",
        "mktWarnTpCd": "00",
        "haltYn": "N",
        "isuPrc": null,
        "uplmtprc": 656500,
        "lwlmtprc": 353500,
        "sbPrc": 353500,
        "listShrs": 22919466,
        "regulssQtyUnit": 1,
        "mktcapScaleCd": 2,
        "kospiYn": "N",
        "invstcautnRemndIsuYn": "N",
        "srttrmOverheatIsuTpCd": "0",
        "secugrpId": "ST",
        "smeYn": "N",
        "krx100IsuYn": "Y",
        "creditOrdPosblYn": "N",
        "adjStkprcCalcYn": "N",
        "idxIndMidclssCd": 72
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**              | **Type**   | **Description**  | ​                                                                                                                                            |
| --------------------- | ---------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| trdDd                 | string(8)  | 체결일자, 거래일자, 매매일자 | YYYYMMDD                                                                                                                                     |
| isuCd                 | string(12) | 종목코드             | ​                                                                                                                                            |
| isuSrtCd              | string(9)  | 종목단축코드           | 예) KR7000660001 → 000660                                                                                                                     |
| isuKorAbbrv           | string(40) | 종목한글약명           | 가나다                                                                                                                                          |
| isuEngNm              | string(80) | 종목명(영문)          |                                                                                                                                              |
| secugrpId             | string(2)  | 증권그룹ID           | ST:주권, MF:증권투자회사, RT:부동산투자회사, SC:선박투자회사,IF:사회간접자본투융자회사, DR:주식예탁증서, EW:ELW, EF:ETF,SW:신주인수권증권, SR:신주인수권증서, BC:수익증권, FE:해외ETF, FS:외국주권, EN:ETN |
| mktWarnTpCd           | string(2)  | 시장경보구분코드         | 00:해당없음(시장경보가 지정될 수 있는 종목에 대해서 지정된 바가 없음을 의미), 01:투자주의, 02:투자경고, 03:투자위험                                                                     |
| admisuYn              | string(1)  | 관리종목여부           | Y:관리 N:일반                                                                                                                                    |
| haltYn                | string(1)  | 거래정지여부           | Y, N                                                                                                                                         |
| idxIndMidclssCd       | string(3)  | 지수업종중분류코드        | 업종분류, 상세코드는 코드표(업종) 참고                                                                                                                       |
| mktcapScaleCd         | string(1)  | 시가총액규모코드         | 유가 (0:제외 1:대 2:중 3:소) / 코스닥 (0:제외 1:KOSDAQ100 2:KOSDAQmid300 3:KOSDAQsmall)                                                                  |
| mfindYn               | string(1)  | 제조업여부            | Y, N (유가)제조업여부                                                                                                                               |
| smeYn                 | string(1)  | 중소기업여부           | Y, N (코스닥)중소기업여부                                                                                                                             |
| krx100IsuYn           | string(1)  | KRX100종목여부       | Y, N                                                                                                                                         |
| kospiYn               | string(1)  | KOSPI여부          | Y,N (유가)KOSPI100여부 (코스닥)프리미어여부                                                                                                               |
| kospi100Yn            | string(1)  | KOSPI100여부       | Y, N (유가)KOSPI여부                                                                                                                             |
| kospi50Yn             | string(1)  | KOSPI50여부        | Y, N (유가)KOSPI50여부                                                                                                                           |
| basPrc                | number(11) | 기준가격,기준가액        |                                                                                                                                              |
| prevddClsprc          | number(11) | 전일종가             |                                                                                                                                              |
| prevddAccTrdvol       | number(12) | 상장중최저가일자         |                                                                                                                                              |
| prevddAccTrdval       | number(22) | 전일누적거래대금         |                                                                                                                                              |
| uplmtprc              | number(11) | 상한가              |                                                                                                                                              |
| lwlmtprc              | number(11) | 하한가              |                                                                                                                                              |
| sbPrc                 | number(11) | 대용가격             | ST,FS,DR,MF,RT,SC,IF,ET,FE,BC,EN 만 해당                                                                                                        |
| parval                | number(11) | 액면가              | 외국주권일 경우 소숫점셋째자리까지 표현가능/코스닥의 각국의 최소화폐단위 표시는 유가기준으로 통일 ※ST,FS,RT,SC,BC만 해당                                                                    |
| isuPrc                | number(11) | 발행가격             | ELW, 신주인수권증서 포함                                                                                                                              |
| listDd                | string(8)  | 상장일자             | YYYYMMDD                                                                                                                                     |
| listShrs              | number(16) | 상장주식수,상장증권수      |                                                                                                                                              |
| arrantrdYn            | string(1)  | 정리매매여부           |                                                                                                                                              |
| creditOrdPosblYn      | string(1)  | 신용주문가능여부         | Y, N                                                                                                                                         |
| regulssQtyUnit        | number(6)  | 정규장매매수량단위        |                                                                                                                                              |
| invstcautnRemndIsuYn  | string(1)  | 투자주의환기종목여부       | Y, N                                                                                                                                         |
| srttrmOverheatIsuTpCd | string(1)  | 단기과열종목구분코드       | 0: 해당없음, 1: 지정예고, 2: 지정, 3: 지정연장(해제연기)                                                                                                       |
| eps                   | number(11) | 주당순이익            |                                                                                                                                              |
| per                   | number(11) | 주가수익률            |                                                                                                                                              |
| bps                   | number(11) | 주당순자산가치          |                                                                                                                                              |
| pbr                   | number(11) | 주당순자산비율          |                                                                                                                                              |
| dps                   | number(11) | 주당배당금액           |                                                                                                                                              |
| divYd                 | number(11) | 배당수익율            |                                                                                                                                              |
| acntclsCd             | string(12) | 결산월구분            | 월별 Map 구조 (001001001001 => 3,6,9,12 월)                                                                                                       |
| adjStkprcCalcYn       | string(1)  | 수정주가산출여부         | Y, N                                                                                                                                         |
| prevddNav             | number(22) | 전일순자산가치          | ETF종목일 경우 소수점 2자리로 표현, 일반종목은 0                                                                                                               |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/247540/master'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "prevddClsprc": 505000,
        "prevddAccTrdvol": 244181,
        "prevddAccTrdval": 122258221700,
        "prevddNav": 0,
        "trdDd": 20220602,
        "acntclsMm": "12",
        "acntclsCd": "000000000001",
        "eps": 4599,
        "bps": 23807,
        "per": 109.31,
        "pbr": 21.12,
        "divYd": 0.2,
        "basPrc": 505000,
        "arrantrdYn": "N",
        "isuKorAbbrv": "에코프로비엠",
        "isuEngNm": "ECOPROBM",
        "isuCd": "KR7247540008",
        "listDd": 20190305,
        "mfindYn": "N",
        "kospi100Yn": "0",
        "kospi50Yn": " -",
        "parval": 500,
        "dps": 920,
        "admisuYn": "N",
        "mktWarnTpCd": "00",
        "haltYn": "N",
        "isuPrc": null,
        "uplmtprc": 656500,
        "lwlmtprc": 353500,
        "sbPrc": 353500,
        "listShrs": 22919466,
        "regulssQtyUnit": 1,
        "mktcapScaleCd": 2,
        "kospiYn": "N",
        "invstcautnRemndIsuYn": "N",
        "srttrmOverheatIsuTpCd": "0",
        "secugrpId": "ST",
        "smeYn": "N",
        "krx100IsuYn": "Y",
        "creditOrdPosblYn": "N",
        "adjStkprcCalcYn": "N",
        "idxIndMidclssCd": 72
    }
}
```



## KOSDAQ 주식종목 마스터(요구형) API  <a href="#api" id="api"></a>

* 주식 종목별 마스터(배치) 정보에 대해 종목별 요청한 데이타 항목만 조회결과로 전송
* 주식종목마스터(master) 대비 다양한 종목기본정보를 제공 등\
  최고가, 대차, 이동평균등 총 85개 항목 제공
* 고객 추가 요구사항 발생시 API 변경을 최소화하여 추가 데이타 제공
* 사용 방법 예) 에코프로비엠 전일종가와 52주최고가격만 조회하고자 할 경우 GET `/v3/market/closed/kosdaq/247540/selectivemaster?prevddClsprc&wk52HgstPrc`
* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/{issuecode}/selectivemaster" method="get" summary="/v3/market/closed/kosdaq/{issuecode}/selectivemaster" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)247540
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "prevddClsprc": 505000
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**              | **Type**       | **Description** |                                                                                                                                                   | **제공구분**                        |
| --------------------- | -------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| trdDd                 | string(8)      | 체결일자,거래일자,매매일자  |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| isuCd                 | string(12)     | 종목코드            | 표준코드                                                                                                                                              | \~/master, \~/selectivemaster   |
| isuSrtCd              | string(9)      | 종목단축코드          | 예) KR7000660001 → 000660                                                                                                                          | \~/master, \~/selectivemaster   |
| isuKorAbbrv           | string(40)     | 종목한글약명          | 가나다                                                                                                                                               | \~/master, \~/selectivemaster   |
| secugrpId             | string(2)      | 증권그룹ID          | ST:주권 MF:증권투자회사 RT:부동산투자회사 SC:선박투자회사 IF:사회간접자본투융자회사 DR:주식예탁증서 EW:ELW EF:ETF SW:신주인수권증권 SR:신주인수권증서 BC:수익증권 FE:해외ETF FS:외국주권 EN:ETN 2014.11.17&#xD; | \~/master, \~/selectivemaster   |
| mktWarnTpCd           | string(2)      | 시장경보구분코드        | 00:해당없음(시장경보가 지정될 수 있는 종목에 대해서 지정된 바가 없음을 의미) 01:투자주의 02:투자경고 03:투자위험&#xD;                                                                        | \~/master, \~/selectivemaster   |
| admisuYn              | string(1)      | 관리종목여부          | Y:관리 N:일반                                                                                                                                         | \~/master, \~/selectivemaster   |
| haltYn                | string(1)      | 거래정지여부          | Y, N                                                                                                                                              | \~/master, \~/selectivemaster   |
| idxIndMidclssCd       | string(3)      | 지수업종중분류코드       | 업종분류, 상세코드는 업종코드표 참고                                                                                                                              | \~/master, \~/selectivemaster   |
| mktcapScaleCd         | string(1)      | 시가총액규모코드        | 유가(0:제외 1:대 2:중 3:소) 코스닥(0:제외 1:KOSDAQ100 2:KOSDAQmid300 3:KOSDAQsmall)                                                                           | \~/master, \~/selectivemaster   |
| mfindYn               | string(1)      | 제조업여부           | Y, N (유가)제조업여부                                                                                                                                    | \~/master, \~/selectivemaster   |
| smeYn                 | string(1)      | 중소기업여부          | Y, N (코스닥)중소기업여부                                                                                                                                  | \~/master, \~/selectivemaster   |
| krx100IsuYn           | string(1)      | KRX100종목여부      | Y, N                                                                                                                                              | \~/master, \~/selectivemaster   |
| kospiYn               | string(1)&#xD; | KOSPI여부         | Y, N (유가)KOSPI100여부,(코스닥)프리미어여부, 프리미어여부 추가 2009.11.16                                                                                             | \~/master, \~/selectivemaster   |
| kospi100Yn            | string(1)&#xD; | KOSPI100여부      | Y, N (유가)KOSPI여부                                                                                                                                  | \~/master, \~/selectivemaster   |
| kospi50Yn             | string(1)&#xD; | KOSPI50여부       | Y, N (유가)KOSPI50여부                                                                                                                                | \~/master, \~/selectivemaster   |
| basPrc                | number(11)     | 기준가격,기준가액       |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| prevddClsprc          | number(11)     | 전일종가            |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| prevddAccTrdvol       | number(11)     | 상장중최저가일자        |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| prevddAccTrdval       | number(22)     | 전일누적거래대금        |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| uplmtprc              | number(11)     | 상한가             |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| lwlmtprc              | number(11)     | 하한가             |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| sbPrc                 | number(11)     | 대용가격            | ST,FS,DR,MF,RT,SC,IF,ET,FE,BC,EN 만 해당 2014.11.17                                                                                                  | \~/master, \~/selectivemaster   |
| parval                | number(11)     | 액면가             | 9(9)V9(3) 외국주권일 경우 소숫점셋째자리까지 표현가능 / 코스닥의 각국의 최소화폐단위 표시는 유가기준으로 통일 / ※ST,FS,RT,SC,BC만 해당"                                                          | \~/master, \~/selectivemaster   |
| isuPrc                | number(11)     | 발행가격            | 신주인수권증서 포함                                                                                                                                        | \~/master, \~/selectivemaster   |
| listDd                | string(8)      | 상장일자            | YYYYMMDD                                                                                                                                          | \~/master, \~/selectivemaster   |
| listShrs              | number(16)     | 상장주식수,상장증권수     |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| arrantrdYn            | string(1)      | 정리매매여부          |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| creditOrdPosblYn      | string(1)      | 신용주문가능여부        | Y, N                                                                                                                                              | \~/master, \~/selectivemaster   |
| regulssQtyUnit        | number(6)      | 정규장매매수량단위       |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| invstcautnRemndIsuYn  | string(1)      | 투자주의환기종목여부      | Y, N                                                                                                                                              | \~/master, \~/selectivemaster   |
| srttrmOverheatIsuTpCd | string(1)      | 단기과열종목구분코드      | 0:해당없음 /1:지정예고 /2:지정 /3:지정연장(해제연기) 2012.11.05 추가                                                                                                  | \~/master, \~/selectivemaster   |
| eps                   | number(11)     | 주당순이익           |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| per                   | number(11)     | 주가수익률           |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| bps                   | number(11)     | 주당순자산가치         |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| pbr                   | number(11)     | 주당순자산비율         |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| dps                   | number(11)     | 주당배당금액          |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| divYd                 | number(11)     | 배당수익율           |                                                                                                                                                   | \~/master, \~/selectivemaster   |
| acntclsCd             | string(12)     | 결산월구분           | 월별 Map 구조 (001001001001 => 3,6,9,12 월)                                                                                                            | \~/master, \~/selectivemaster   |
| adjStkprcCalcYn       | string(1)      | 수정주가산출여부        | Y, N                                                                                                                                              | \~/master, \~/selectivemaster   |
| prevddNav             | number(22)     | 전일순자산가치         | ETF종목일 경우 소수점 2자리로 표현, 일반종목은 0                                                                                                                    | \~/master, \~/selectivemaster   |
| srtsellTrdVol         | number(11)     | 공매도거래량          | 공매도거래량(주식수, 전일기준)                                                                                                                                 | \~/shortsell,\~/selectivemaster |
| srtsellTrdAmt         | number(11)     | 공매도거래금액         | 공매도거래금액(주식수, 전일기준)                                                                                                                                | \~/shortsell,\~/selectivemaster |
| lendBalQty            | number(11)     | 대차잔고수량          | 대차잔고수량(주식수, 전일기준)                                                                                                                                 | \~/shortsell,\~/selectivemaster |
| lendBalAmt            | number(11)     | 대차잔고금액          | 단위 1,000 원                                                                                                                                        | \~/shortsell,\~/selectivemaster |
| srtsellOverheatDd     | number(8)      | 공매도과열종목지정일      | 공매도 과열종목일 경우 값을 가짐                                                                                                                                | \~/selectivemaster 요구형만 제공      |
| dd3AvgPrc             | number(11)     | 전일가격3일이동평균      | 개별종목                                                                                                                                              | \~/selectivemaster 요구형만 제공      |
| dd5AvgPrc             | number(11)     | 전일가격5일이동평균      | 개별종목, 지수                                                                                                                                          | \~/selectivemaster 요구형만 제공      |
| dd10AvgPrc            | number(11)     | 전일가격10일이동평균     | 개별종목, 지수                                                                                                                                          | \~/selectivemaster 요구형만 제공      |
| dd20AvgPrc            | number(11)     | 전일가격20일이동평균     | 개별종목, 지수                                                                                                                                          | \~/selectivemaster 요구형만 제공      |
| dd40AvgPrc            | number(11)     | 전일가격40일이동평균     | 개별종목                                                                                                                                              | \~/selectivemaster 요구형만 제공      |
| dd60AvgPrc            | number(11)     | 전일가격60일이동평균     | 개별종목, 지수                                                                                                                                          | \~/selectivemaster 요구형만 제공      |
| dd120AvgPrc           | number(11)     | 전일가격120일이동평균    | 개별종목, 지수                                                                                                                                          | \~/selectivemaster 요구형만 제공      |
| dd250AvgPrc           | number(11)     | 전일가격250일이동평균    | 개별종목                                                                                                                                              | \~/selectivemaster 요구형만 제공      |
| dd3AvgTrdVol          | number(11)     | 전일거래량3일이동평균     |                                                                                                                                                   | \~/selectivemaster 요구형만 제공      |
| dd5AvgTrdVol          | number(11)     | 전일거래량5일이동평균     |                                                                                                                                                   | \~/selectivemaster 요구형만 제공      |
| dd10AvgTrdVol         | number(11)     | 전일거래량10일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공      |
| dd20AvgTrdVol         | number(11)     | 전일거래량20일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd40AvgTrdVol         | number(11)     | 전일거래량40일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd60AvgTrdVol         | number(11)     | 전일거래량60일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd120AvgTrdVol        | number(11)     | 전일거래량120일이동평균   |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd250AvgTrdVol        | number(11)     | 전일거래량250일이동평균   |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd3AvgTrdAmt          | number(11)     | 전일거래대금3일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd5AvgTrdAmt          | number(11)     | 전일거래대금5일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd10AvgTrdAmt         | number(11)     | 전일거래대금10일이동평균   |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd20AvgTrdAmt         | number(11)     | 전일거래대금20일이동평균   |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd40AvgTrdAmt         | number(11)     | 전일거래대금40일이동평균   |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd60AvgTrdAmt         | number(11)     | 전일거래대금60일이동평균   |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd120AvgTrdAmt        | number(11)     | 전일거래대금120일이동평균  |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd250AvgTrdAmt        | number(11)     | 전일거래대금250일이동평균  |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd5AvgDp              | number(11)     | 전일이격도5일이동평균     |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd20AvgDp             | number(11)     | 전일이격도20일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd60AvgDp             | number(11)     | 전일이격도60일이동평균    |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| dd120AvgDp            | number(11)     | 전일이격도120일이동평균   |                                                                                                                                                   | \~/selectivemaster 요구형만 제공&#xD; |
| BzDd                  | number(11)     | 영업일             | 시장별 최종가동일, 입회일(오늘일 경우 정상시장 가동)&#xD;                                                                                                               | \~/selectivemaster 요구형만 제공&#xD; |
| IsuEngNm              | string(80)     | 종목명(영문)         |                                                                                                                                                   | \~/selectivemaster 요구형만 제공      |
| wk52HgstPrc           | number(11)     | 52주최고가격         |                                                                                                                                                   |                                 |
| wk52LwstPrc           | number(11)     | 52주최저가격         |                                                                                                                                                   |                                 |
| wk52HgstprcDd         | number(8)      | 52주최고가일자        |                                                                                                                                                   |                                 |
| wk52LwstprcDd         | number(8)      | 52주최저가일자        |                                                                                                                                                   |                                 |
| wk52HgstTrdvol        | number(11)     | 52주최고거래량        |                                                                                                                                                   |                                 |
| wk52LwstTrdvol        | number(11)     | 52주최저거래량        |                                                                                                                                                   |                                 |
| liquShrs              | number(16)     | 유동주식수           |                                                                                                                                                   |                                 |
| DebtRt                | number(11)     | 부채비율            | 부채비율 소수점 2자리 형태                                                                                                                                   |                                 |
| CrdtGrd               | string(64)     | 신용등급            |                                                                                                                                                   |                                 |
| Cap                   | number(11)     | 자본금             |                                                                                                                                                   |                                 |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/247540/selectivemaster'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "prevddClsprc": 505000
    }
}
```



## KOSDAQ 주식종목 종가 API  <a href="#api" id="api"></a>

* 제공시간 : 전일,당일 PM 15:40 이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/{issuecode}/closeprice" method="get" summary="/v3/market/closed/kosdaq/{issuecode}/closeprice" %}
{% swagger-description %}
종목 당일 종가제공
{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)247540
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "trdPrc": 503200,
        "cmpprevddTpCd": "5",
        "opnprc": 500700,
        "hgprc": 505100,
        "lwprc": 496100,
        "accTrdvol": 100002,
        "accTrdval": 50129874200,
        "cmpprevddPrc": -1800
    }
}
```
{% endswagger-response %}

{% swagger-response status="400" description="" %}
```
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**      | **Type**   | **Description** |                                                      |
| ------------- | ---------- | --------------- | ---------------------------------------------------- |
| isuSrtCd      | String(9)  | 종목단축코드          | 예) KR7000660001 → 000660                             |
| cmpprevddTpCd | String(1)  | 전일대비구분코드        | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc  | number(11) | 전일대비가격          | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0                     |
| opnprc        | number(11) | 시가              | 단위:원                                                 |
| hgprc         | number(11) | 고가              | 단위:원                                                 |
| lwprc         | number(11) | 저가              | 단위:원                                                 |
| trdPrc        | number(11) | 체결가격            |                                                      |
| accTrdvol     | number(12) | 누적체결수량,누적거래량    | 단위:주                                                 |
| accTrdval     | number(22) | 누적거래대금          | 단위:원                                                 |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/247540/closeprice'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "trdPrc": 503200,
        "cmpprevddTpCd": "5",
        "opnprc": 500700,
        "hgprc": 505100,
        "lwprc": 496100,
        "accTrdvol": 100002,
        "accTrdval": 50129874200,
        "cmpprevddPrc": -1800
    }
}
```

## KOSDAQ 지수  <a href="#api" id="api"></a>

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/index" method="get" summary="/v3/market/closed/kosdaq/index" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "Q1",
        "isuCnt": 1556,
        "trdPrc": 890.11,
        "cmpprevddTpCd": "5",
        "opnprc": 890.47,
        "hgprc": 892.98,
        "lwprc": 888.45,
        "accTrdvol": 1052988,
        "accTrdval": 5777766,
        "mktcap": 394085835,
        "cmpprevddPrc": -3.25,
        "listShrs": 46123757
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### **Response Parameters**

| **Name**      | **Type**   | **Description** |                                                      |
| ------------- | ---------- | --------------- | ---------------------------------------------------- |
| isuSrtCd      | String(9)  | 종목단축코드          | 예) KR7000660001 → 000660                             |
| cmpprevddTpCd | String(1)  | 전일대비구분코드        | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc  | number(11) | 전일대비가격          | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0                     |
| opnprc        | number(11) | 시가              | 단위:원                                                 |
| hgprc         | number(11) | 고가              | 단위:원                                                 |
| lwprc         | number(11) | 저가              | 단위:원                                                 |
| trdPrc        | number(11) | 체결가격            |                                                      |
| accTrdvol     | number(12) | 누적체결수량,누적거래량    | 단위:주                                                 |
| accTrdval     | number(22) | 누적거래대금          | 단위:원                                                 |
| isuCnt        | number(16) | 종목수             |                                                      |
| listShrs      | number(16) | 상장주식수,상장증권수     | 업종상장주식수 단위는  천주, 그외는 1주                              |
| mktcap        | number(22) | 시가총액            | 단위: 업종-백만                                            |

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/index'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "Q1",
        "isuCnt": 1556,
        "trdPrc": 890.11,
        "cmpprevddTpCd": "5",
        "opnprc": 890.47,
        "hgprc": 892.98,
        "lwprc": 888.45,
        "accTrdvol": 1052988,
        "accTrdval": 5777766,
        "mktcap": 394085835,
        "cmpprevddPrc": -3.25,
        "listShrs": 46123757
    }
}
```

## KOSDAQ 주식 공매도 일별조회 API  <a href="#api" id="api"></a>

* 제공시간 : 전일,당일 18:00 이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/{issuecode}/shortsell" method="get" summary="/v3/market/closed/kosdaq/{issucode}/shortsell" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)247540
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" type="string" required="true" %}
조회시작일자
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqEndDd" type="string" required="true" %}
조회종료일자
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "hisLists": [
            {
                "trdDd": 20220503,
                "lendBalQty": 2398180,
                "lendBalAmt": 1225469980,
                "srtsellBal": 588890,
                "srtsellTrdVol": 17491,
                "srtsellTrdAmt": 8872884900
            },
            {
                "trdDd": 20220502,
                "lendBalQty": 2439030,
                "lendBalAmt": 1195124700,
                "srtsellBal": 562224,
                "srtsellTrdVol": 26917,
                "srtsellTrdAmt": 13038232800
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

**Response Parameter**

| **Name**      | **Type**   | **Description** |                          |
| ------------- | ---------- | --------------- | ------------------------ |
| isuSrtCd      | string(9)  | 종목단축코드          | 예) KR7000660001 → 000660 |
| hisLists      | Array(4)   | 과거리스트           |                          |
| trdDd         | string(8)  | 체결일자,거래일자,매매일자  | YYYYMMDD                 |
| srtsellTrdvol | number(11) | 공매도거래량          | 공매도거래량(주식수, 전일기준)        |
| srtsellTrdAmt | number(11) | 공매도거래금액         | 공매도거래금액(주식수, 전일기준)       |
| lendBalQty    | number(11) | 대차잔고수량          | 대차잔고수량(주식수, 전일기준)        |
| lendBalAmt    | number(11) | 대차잔고금액          | 단위 1,000 원               |

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/247540/shortsell?inqStrtDd=20181001&inqEndDd=20181231'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "hisLists": [
            {
                "trdDd": 20220503,
                "lendBalQty": 2398180,
                "lendBalAmt": 1225469980,
                "srtsellBal": 588890,
                "srtsellTrdVol": 17491,
                "srtsellTrdAmt": 8872884900
            },
            {
                "trdDd": 20220502,
                "lendBalQty": 2439030,
                "lendBalAmt": 1195124700,
                "srtsellBal": 562224,
                "srtsellTrdVol": 26917,
                "srtsellTrdAmt": 13038232800
            }
        ]
    }
}
```



## KOSDAQ 주식 외국인 보유율 히스토리 API

* 종목 외국인 보유율 과거 데이터 제공
* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/{issuecode}/foreignhistory" method="get" summary="/v3/market/closed/kosdaq/{issucode}/foreignhistory" %}
{% swagger-description %}
최대 100건 까지만 조회 가능
{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" type="string" required="true" %}
조회시작일자 (YYYYMMDD)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqEndDd" type="string" required="true" %}
조회종료일자
{% endswagger-parameter %}

{% swagger-parameter in="query" name="reqCnt" type="number" %}
요청건수 (최대100건)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "hisLists": [
            {
                "FornHdVol": 2340232,
                "cmpprevddFornHdVol": -8698,
                "FornHdVolRt": 10.21,
                "trdDd": 20220503
            },
            {
                "FornHdVol": 2348930,
                "cmpprevddFornHdVol": 9281,
                "FornHdVolRt": 10.25,
                "trdDd": 20220502
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**           | **Type**   | **Description** |   |
| ------------------ | ---------- | --------------- | - |
| isuSrtCd           | String(9)  | 종목단축코드          |   |
| hisLists           | Array(4)   | 과거리스트           |   |
| trdDd              | string(8)  | 체결일자,거래일자,매매일자  |   |
| FornHdVol          | number(11) | 외국인보유주식수        |   |
| cmpprevddFornHdVol | number(11) | 외국인보유주식수전일대비    |   |
| FornHdVolRt        | number(5)  | 외국인보유율          |   |

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/247540/foreignhistory?inqStrtDd=20181001&inqEndDd=20181231&reqCnt=20'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "hisLists": [
            {
                "FornHdVol": 2340232,
                "cmpprevddFornHdVol": -8698,
                "FornHdVolRt": 10.21,
                "trdDd": 20220503
            },
            {
                "FornHdVol": 2348930,
                "cmpprevddFornHdVol": 9281,
                "FornHdVolRt": 10.25,
                "trdDd": 20220502
            }
        ]
    }
}
```



## KOSDAQ 주식 종목 히스토리 API

* 종목 일별 과거 데이터 제공
* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/kosdaq" path="/{issuecode}/history" method="get" summary="/v3/market/closed/kosdaq/{issuecode}/history" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드
{% endswagger-parameter %}

{% swagger-parameter in="query" name="trnsmCycleTpCd" type="string" required="true" %}
전송주기구분코드 (D:일별, W:주별, M:월별) 해당기간의 마지막영업일 기준시세. ex) W:주-금요일, M:월-31일
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" type="string" required="true" %}
조회시작일자 (YYYYMMDD)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqEndDd" type="string" required="true" %}
조회종료일자 (YYYYMMDD)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="reqCnt" type="number" %}
요청건수 (최대 100건)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "hisLists": [
            {
                "trdDd": 20220503,
                "trdPrc": 503619,
                "cmpprevddTpCd": "2",
                "opnprc": 488934,
                "hgprc": 504999,
                "lwprc": 488836,
                "accTrdvol": 337130,
                "accTrdval": 170866691500,
                "cmpprevddPrc": 20696
            },
            {
                "trdDd": 20220502,
                "trdPrc": 482922,
                "cmpprevddTpCd": "2",
                "opnprc": 465971,
                "hgprc": 484203,
                "lwprc": 464098,
                "accTrdvol": 265195,
                "accTrdval": 128353745900,
                "cmpprevddPrc": 13403
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**      | **Type**   | **Description** |                                                      |
| ------------- | ---------- | --------------- | ---------------------------------------------------- |
| isuSrtCd      | String(3)  | 종목단축코드          |                                                      |
| hisLists      | Array(4)   | 과거리스트           |                                                      |
| trdDd         | string(8)  | 체결일자,거래일자,매매일자  | YYYYMMDD                                             |
| trdPrc        | number(11) | 체결가격            |                                                      |
| cmpprevddTpCd | string(1)  | 전일대비구분코         | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc  | number(11) | 전일대비가격          | 단위:원 / 신주인수권 증서,증권의 신규 상장 당일 : 0                     |
| accTrdvol     | number(12) | 누적체결수량,누적거래량    | 단위:주                                                 |
| accTrdval     | number(22) | 누적거래대금          | 단위:원                                                 |
| opnprc        | number(11) | 시가              | 단위:원                                                 |
| hgprc         | number(11) | 고가              | 단위:원                                                 |
| lwprc         | number(11) | 저가              | 단위:원                                                 |

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e34448c982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/kosdaq/247540/history?trnsmCycleTpCd=D&inqStrtDd=20181001&inqEndDd=20181231&reqCnt=5'
```

#### Response Example

```bash
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "247540",
        "hisLists": [
            {
                "trdDd": 20220503,
                "trdPrc": 503619,
                "cmpprevddTpCd": "2",
                "opnprc": 488934,
                "hgprc": 504999,
                "lwprc": 488836,
                "accTrdvol": 337130,
                "accTrdval": 170866691500,
                "cmpprevddPrc": 20696
            },
            {
                "trdDd": 20220502,
                "trdPrc": 482922,
                "cmpprevddTpCd": "2",
                "opnprc": 465971,
                "hgprc": 484203,
                "lwprc": 464098,
                "accTrdvol": 265195,
                "accTrdval": 128353745900,
                "cmpprevddPrc": 13403
            }
        ]
    }
}
```

