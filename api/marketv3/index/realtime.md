# KRX업종실시간

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## 업종 시가총액 API  <a href="#api" id="api"></a>

* 전체 업종시가총액 (KOSPI/KOSDAQ지수 포함)
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/index" path="/{marketcode}/{issuecode}/marketcap" method="get" summary="/v3/market/realtime/index/{marketcode}/{issuecode}/marketcap" %}
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
        "accTrdvol": 455824,
        "accTrdval": 5810909,
        "mktcap": 2101999310,
        "listShrs": 62187655
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**  | **Type**   | **Description** |                         |
| --------- | ---------- | --------------- | ----------------------- |
| isuSrtCd  | String(3)  | 업종코드            | 업종코드표 참조                |
| isuCnt    | number(16) | 종목수             |                         |
| listShrs  | number(16) | 상장주식수,상장증권수     | 업종상장주식수 단위는  천주, 그외는 1주 |
| accTrdvol | number(12) | 누적체결수량,누적거래량    | 단위:주                    |
| accTrdval | number(22) | 누적거래대금          | 단위:원                    |
| mktcap    | number(22) | 시가총액            | 단위: 업종-백만               |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/index/kospi/K1/marketcap'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "isuCnt": 941,
        "accTrdvol": 455824,
        "accTrdval": 5810909,
        "mktcap": 2101999310,
        "listShrs": 62187655
    }
}
```



## 업종 예상지수 API  <a href="#api" id="api"></a>

* 전체 업종예상지수 (KOSPI/KOSDAQ지수 포함)
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/index" path="/{marketcode}/{issuecode}/prospectindex" method="get" summary="/v3/market/realtime/index/{marketcode}/{issuecode}/prospectindex" %}
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
        "deemTm": "9000000",
        "deemTrdPrc": 2676.94,
        "deemAccTrdvol": 6129,
        "deemcmpprevddPrc": 17.95,
        "deemcmpprevddTpCd": "69",
        "deemAccTrdval": 88515
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**          | **Type**   | **Description** |                                                      |
| ----------------- | ---------- | --------------- | ---------------------------------------------------- |
| isuSrtCd          | String(3)  | 업종코드            | 업종코드표 참조                                             |
| deemTm            | String(8)  | 예상체결시각          | HHMMSSmm                                             |
| deemTrdPrc        | number(10) | 예상지수            |                                                      |
| deemcmpprevddTpCd | String(1)  | 예상전일대비구분코드      | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| deemcmpprevddPrc  | number(10) | 예상전일대비지수        |                                                      |
| deemAccTrdvol     | number(12) | 예상누적체결수량        | 단위:주                                                 |
| deemAccTrdval     | number(12) | 예상누적거래대금        | 단위:원                                                 |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/index/kospi/K1/prospectindex'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "deemTm": "9000000",
        "deemTrdPrc": 2676.94,
        "deemAccTrdvol": 6129,
        "deemcmpprevddPrc": 17.95,
        "deemcmpprevddTpCd": "69",
        "deemAccTrdval": 88515
    }
}
```









