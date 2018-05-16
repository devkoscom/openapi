# GET - 테이블 외부

KOSPI/KOSDAQ등의 지수 예상지수 및 업종별 투자자별 거래량등을 제공한다.  


## Syntax

HTTP methods   \|   **GET**

Authentication    \|   **API Key**



{% hint style="info" %}
업종지수 스트리밍 조회는 xx를 참고하세요.
{% endhint %}

{% hint style="warning" %}
`marketcode` 및 `issuecode` 는 [코드표 &gt; "시장코드표"](https://koscom.gitbook.io/open-api/untitled-1/undefined-8#undefined)를 참조하세요.
{% endhint %}







## 업종 종가 API

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

#### Response Parameters {#request-parameters}

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- |
| fundcode | String\(20\) | 펀드표준코드 |  |
| fundName | Number\(1\) | 펀드이름 |  |
| valAtTrade | ​string\(11\) | 잔고거래내역 | \*테이블 하단 참고 |
| varAtCur | string\(5\)​ | 잔고구분 | \*테이블 하단 참고 |
| qrToDate | String\(12\) | 조회종료날짜 | YYYYMMDD |

> `varAtTrade`   
> 첫 요청은 null\(“null”\)로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청하며, ALL인 경우는 page없이 일괄전송이므로 본 필드는 의미 없음
>
> `varAtCur`   
> NRM\(일반/현금\), CRD\(신용\), LOAN\(대출\), SUM \(분류가 불가한 경우 구분 없이 합산한 경우며 대출잔고는 제외\)







## 주식종목 마스터 API

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/stocks" path="/{marketcode}/{issuecode}/master" %}
{% api-method-summary %}
/v2/market/stocks/{marketcode}/{issuecode}/master
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장구분 \(kospi \| kosdaq\)
{% endapi-method-parameter %}

{% api-method-parameter name="issuecode" type="string" required=true %}
종목코드 ex\)005930
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
| secugrpId | string\(2\) | 증권그룹ID | \*테이블하단참고 |
| mktWarnTpCd | string\(2\) | 시장경보구분코드 | \*테이블하단참고 |
| admisuYn | string\(1\) | 관리종목여부 | Y:관리 N:일반 |
| haltYn | string\(1\) | 거래정지여부 | Y, N  |
| idxIndMidclssCd | string\(3\) | 지수업종중분류코드 | 코드표&gt; 업종코드표 참고
| mktcapScaleCd | string\(1\) | 시가총액규모코드 | \*테이블하단참고 |
| mfindYn | string\(1\) | 제조업여부 | Y, N \(유가\)제조업여부 |
| smeYn | string\(1\) | 중소기업여부 | Y, N \(코스닥\)중소기업여부 |
| 업종 | string\(1\) | KRX100종목여부 | Y, N \(유가\)KOSPI100여부 / \(코스닥\)프리미어여부
| kospiYn | string\(1\) | KOSPI여부 | Y, N
| kospi100Yn | string\(1\) | KOSPI100여부 | Y, N \(유가\)KOSPI여부 |
| kospi50Yn | string\(1\) | KOSPI50여부 | Y, N \(유가\)KOSPI50여부 |
| basPrc | number\(11\) | 기준가격,기준가액 |  |
| prevddClsprc | number\(11\) | 전일종가 |  |
| prevddAccTrdvol | number\(12\) | 상장중최저가일자 |  |
| prevddAccTrdval | number\(22\) | 전일누적거래대금 |  |
| uplmtprc | number\(11\) | 상한가 |  |
| lwlmtprc | number\(11\) | 하한가 |  |
| sbPrc | number\(11\) | 대용가격 | ST, FS, DR, MF, RT, SC ,IF ,ET, FE, BC, EN 만 해당 
| parval | number\(11\) | 액면가 | \*테이블하단참고 |
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
| acntclsCd | string\(12\) | 결산월구분 | 월별 Map 구조 \(001001001001 -&gt; 3,6,9,12 월\) |
| adjStkprcCalcYn | string\(1\) | 수정주가산출여부 | Y, N |
| prevddNav | number\(22\) | 전일순자산가치 | ETF종목일 경우 소수점 2자리, 일반종목은 0 |

> `secugrpId`   
> ST:주권, MF:증권투자회사, RT:부동산투자회사, SC:선박투자회사,
>
> `mktWarnTpCd`  
> 00:해당없음\(시장경보가 지정될 수 있는 종목에 대해서 지정된
> 01:투자주의, 02:투자경고, 03:투자위험
>
> `mktcapScaleCd`   
> 유가 \(0:제외 1:대 2:중 3:소\)
> 코스닥 \(0:제외 1:KOSDAQ100 2:KOSDAQmid300 3:KOSDAQsmall\)
>
> `parval`   
> 9\(9\)V9\(3\) 외국주권일 경우 소숫점셋째자리까지 표현가능
> 코스닥의 각국의 최소화폐단위 표시는 유가기준으로 통일
> ST,FS,RT,SC,BC만 해당




