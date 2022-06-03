# KRX업종실시간

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## 업종 시가총액 API  <a href="#api" id="api"></a>

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
```





