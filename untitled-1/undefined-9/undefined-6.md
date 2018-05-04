# 주식 시세조회

주식시장\(유가증권, 코스닥\) 의 종목 리스트, 종목 마스터, 종목 체결, 호가잔량, 종목 투자자별 종가등을 제공한다.



#### URI 입력값

* base URI : [https://sandbox-apigw.koscom.co.kr**/**_**v2/market/stocks/**_](https://sandbox-apigw.koscom.co.kr/v2/market/stocks/)
* `marketcode `: 입력가능 marketcode 리스트  \[**`kospi`**, **`kosdaq`**\]
* `issuecode `: 주식종목의 단축코드



##  주식종목 리스트 API {#api}

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/stocks" path="/{marketcode}/lists" %}
{% api-method-summary %}
 /v2/market/stocks/{marketcode}/lists
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장구분 \(kospi \| kosdaq\)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Syntax {#syntax}

* URI
  *  /v2/market/stocks/**{marketcode}/lists    **
* HTTP methods
  * GET
* Authentication
  * API Key

#### Example {#example}

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}



## 주식종목 마스터 API {#api}

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

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Syntax {#syntax}

* URI
  *  /v2/market/stocks/**{marketcode}/{issuecode}/master**
* HTTP methods
  * GET
* Authentication
  * API Key

#### Example {#example}

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}



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

```

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

#### Syntax {#syntax}

* URI
  *  /v2/market/stocks/**{marketcode}/{issuecode}/closeprice**
* HTTP methods
  * GET
* Authentication
  * API Key

#### Example {#example}

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

#### 응답리스트

| No. | 항목명 | 한글명 | 설명 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | isuSrtCd | 종목단축코드 | 예\) KR7000660001 → 000660 |
| 2 | cmpprevddTpCd | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| 3 | cmpprevddPrc | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| 4 | opnprc | 시가 | 단위:원 |
| 5 | hgprc | 고가 | 단위:원 |
| 6 | lwprc | 저가 | 단위:원 |
| 7 | trdPrc | 체결가 |  |
| 8 | accTrdvol | 누적체결수량,누적거래량 | 단위:주 |
| 9 | accTrdval | 누적거래대금 | 단위:원 |



