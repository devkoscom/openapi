# KRX업종실시간종가

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## 업종 종가 API  <a href="#api" id="api"></a>

* 제공시간 : 전일,당일 15:40 이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/index" path="/{marketcode}/{issuecode}/closeindex" method="get" summary="/v3/market/closed/index/{marketcode}/{issuecode}/closeindex" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" required="true" name="marketcode" %}
ex) kospi
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="issuecode" %}
ex) K1
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "isuCnt": 941,
        "trdPrc": 2670.65,
        "cmpprevddTpCd": "2",
        "opnprc": 2679.57,
        "hgprc": 2681.51,
        "lwprc": 2663,
        "accTrdvol": 552199,
        "accTrdval": 7452658,
        "mktcap": 2101702986,
        "cmpprevddPrc": 11.66,
        "listShrs": 62187655
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```javascript
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
| isuCnt        | number(16) | 종목수             |                                                      |
| listShrs      | number(16) | 상장주식수,상장증권수     | 업종상장주식수 단위는  천주, 그외는 1주                              |
| mktcap        | number(22) | 시가총액            | 단위: 업종-백만                                            |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/index/kospi/K1/closeindex'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "isuCnt": 941,
        "trdPrc": 2670.65,
        "cmpprevddTpCd": "2",
        "opnprc": 2679.57,
        "hgprc": 2681.51,
        "lwprc": 2663,
        "accTrdvol": 552199,
        "accTrdval": 7452658,
        "mktcap": 2101702986,
        "cmpprevddPrc": 11.66,
        "listShrs": 62187655
    }
}
```



## 업종 히스토리 API  <a href="#api" id="api"></a>

* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/index" path="/index/{marketcode}/{issuecode}/history" method="get" summary="/v3/market/closed/index/{marketcode}/{issuecode}/history" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) K1
{% endswagger-parameter %}

{% swagger-parameter in="query" name="trnsmCycleTpCd" required="true" %}
전송주기구분코드 (D:일 W:주 M:월)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" required="true" %}
조회시작일자 YYYYMMSS
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqEndDd" required="true" %}
조회종료일자 YYYYMMSS
{% endswagger-parameter %}

{% swagger-parameter in="query" name="reqCnt" required="false" type="number" %}
요청건수 (최대 100건)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "hisLists": [
            {
                "trdDd": 20220503,
                "trdPrc": 2680.46,
                "cmpprevddTpCd": "5",
                "opnprc": 2690.16,
                "hgprc": 2702.1,
                "lwprc": 2680.46,
                "accTrdvol": 883402,
                "accTrdval": 9199338,
                "cmpprevddPrc": -6.99
            },
            {
                "trdDd": 20220502,
                "trdPrc": 2687.45,
                "cmpprevddTpCd": "5",
                "opnprc": 2669.21,
                "hgprc": 2689.91,
                "lwprc": 2667.85,
                "accTrdvol": 873722,
                "accTrdval": 9075648,
                "cmpprevddPrc": -7.6
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameter

| **Name**      | **Type**   | **Description** |               |
| ------------- | ---------- | --------------- | ------------- |
| isuSrtCd      | String(3)  | 업종코드            | 코드표 >업종코드표 참조 |
| isuKorNm      | String(80) | 종목한글명           |               |
| hisLists      | Array(4)   | 과거리스트           |               |
| trdDd         | string(8)  | 체결일자,거래일자,매매일자  | YYYYMMDD      |
| trdPrc        | number(11) | 체결가격            |               |
| cmpprevddTpCd | string(1)  | 전일대비부호          |               |
| cmpprevddPrc  | number(11) | 전일대비가격          |               |
| accTrdvol     | number(12) | 누적체결수량,누적거래량    |               |
| accTrdval     | number(22) | 누적거래대금          |               |
| opnprc        | number(11) | 시가              |               |
| hgprc         | number(11) | 고가              |               |
| lwprc         | number(11) | 저가              |               |

### Request Example

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/index/kospi/K1/history?trnsmCycleTpCd=D&inqStrtDd=20220501&inqEndDd=20220503&reqCnt=2'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "hisLists": [
            {
                "trdDd": 20220503,
                "trdPrc": 2680.46,
                "cmpprevddTpCd": "5",
                "opnprc": 2690.16,
                "hgprc": 2702.1,
                "lwprc": 2680.46,
                "accTrdvol": 883402,
                "accTrdval": 9199338,
                "cmpprevddPrc": -6.99
            },
            {
                "trdDd": 20220502,
                "trdPrc": 2687.45,
                "cmpprevddTpCd": "5",
                "opnprc": 2669.21,
                "hgprc": 2689.91,
                "lwprc": 2667.85,
                "accTrdvol": 873722,
                "accTrdval": 9075648,
                "cmpprevddPrc": -7.6
            }
        ]
    }
}
```



