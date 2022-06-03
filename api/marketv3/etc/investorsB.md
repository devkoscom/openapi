# 코스닥종목별투자자

주식시장(코스닥시장)의 투자자 관련 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## KOSDAQ 주식종목별 투자자별 매매동향 (종가) API  <a href="#api" id="api"></a>

* 장마감후 종목별투자자별 매매동향
* 제공시간 : 전일,당일 15:30이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/investors/kosdaq" path="/{issuecode}/investors" method="get" summary="/v3/market/investors/kosdaq/{issuecode}/investors" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 247540
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuCd": "KR7247540008",
        "isuSrtCd": "247540",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 13152,
                "askTrdval": 6577969,
                "bidTrdvol": 7469,
                "bidTrdval": 3748374
            },
            {
                "invstCd": "02",
                "askTrdvol": 186,
                "askTrdval": 93462,
                "bidTrdvol": 0,
                "bidTrdval": 0
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response **Parameters**

| **Name**   | **Type**   | **Description**     |
| ---------- | ---------- | ------------------- |
| isuSrtCd   | string(9)  | 종목단축코드              |
| invstLists | Array(4)   | 투자자리스트              |
| invstCd    | string(4)  | 투자자코드 (참조 :투자자코드표') |
| askTrdvol  | number(10) | 매도체결수량,매도거래량        |
| askTrdval  | number(22) | 매도거래대금              |
| bidTrdvol  | number(10) | 매수체결수량,매수거래량        |
| bidTrdval  | number(22) | 매수거래대금              |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/investors/kosdaq/247540/investors'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuCd": "KR7247540008",
        "isuSrtCd": "247540",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 13152,
                "askTrdval": 6577969,
                "bidTrdvol": 7469,
                "bidTrdval": 3748374
            },
            {
                "invstCd": "02",
                "askTrdvol": 186,
                "askTrdval": 93462,
                "bidTrdvol": 0,
                "bidTrdval": 0
            }
        ]
    }
}
```



## KOSDAQ 지수 투자자 마감정보 API  <a href="#api" id="api"></a>

* KOSDAQ 투자자 마감정보 (업종-투자자별 참고)
* 제공시간 : 전일,당일 15:40이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/investors/kosdaq" path="/investors" method="get" summary="/v3/market/investors/kosdaq/investors" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "15303000",
        "isuSrtCd": "Q1",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 1952659,
                "askTrdval": 46008340,
                "bidTrdvol": 3715211,
                "bidTrdval": 88903247
            },
            {
                "invstCd": "02",
                "askTrdvol": 223238,
                "askTrdval": 8422446,
                "bidTrdvol": 252276,
                "bidTrdval": 6941702
            }
        ]
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

#### Response **Parameters**

| **Name**   | **Type**   | **Description** |             |
| ---------- | ---------- | --------------- | ----------- |
| Tm         | string(8)  | 장시간             | HHMMSSmm    |
| invstLists | Array(4)   | 투자자리스트          |             |
| invstCd    | string(4)  | 투자자코드           | '투자자코드표' 참조 |
| askTrdvol  | number(10) | 매도체결수량,매도거래량    |             |
| askTrdval  | number(22) | 매도거래대금          |             |
| bidTrdvol  | number(10) | 매수체결수량,매수거래량    |             |
| bidTrdval  | number(22) | 매수거래대금          |             |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/investors/kosdaq/investors'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "15303000",
        "isuSrtCd": "Q1",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 1952659,
                "askTrdval": 46008340,
                "bidTrdvol": 3715211,
                "bidTrdval": 88903247
            },
            {
                "invstCd": "02",
                "askTrdvol": 223238,
                "askTrdval": 8422446,
                "bidTrdvol": 252276,
                "bidTrdval": 6941702
            }
        ]
    }
}
```





