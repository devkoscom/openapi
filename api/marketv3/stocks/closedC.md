# 주식실시간종가C

주식시장(ETF) 종가 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## 주식종목(ETF) 장마감후 순자산가치 API  <a href="#api" id="api"></a>

* 제공시간 : 전일,당일16:00 이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/etf" path="/{marketcode}/{issuecode}/closenav" method="get" summary="/v3/market/closed/etf/{marketcode}/{issuecode}/closenav" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi, kosdaq
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
주식종목의 단축코드
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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

| **Name**     | **Type**   | **Description** |                             |
| ------------ | ---------- | --------------- | --------------------------- |
| isuSrtCd     | String(9)  | 종목단축코드          | 예) KR7000660001 → 000660    |
| nav          | Number(11) | 순자산가치           | 당일 NAV (ETF종목만 존재, 소수점 2자리) |
| cmpprevddNav | Number(11) | 전일대비순자산가치       |                             |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/etf/kospi/590003/closenav'
```

#### Response Example

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



