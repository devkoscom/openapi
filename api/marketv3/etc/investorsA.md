# 유가종목별투자자

주식시장(유가증권)의 투자자 관련 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## KOSPI 주식종목별 투자자별 매매동향 (종가) API  <a href="#api" id="api"></a>

* 장마감후 종목별투자자별 매매동향
* 제공시간 : 전일,당일 15:30이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/investors/kospi" path="/{issuecode}/investors" method="get" summary="/v3/market/investors/kospi/{issuecode}/investors" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 005930
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuCd": "KR7005930003",
        "isuSrtCd": "005930",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 534814,
                "askTrdval": 35819799,
                "bidTrdvol": 1365197,
                "bidTrdval": 91357237
            },
            {
                "invstCd": "02",
                "askTrdvol": 110469,
                "askTrdval": 7389240,
                "bidTrdvol": 53331,
                "bidTrdval": 3574395
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
'https://testoap.k-mydata.org/v3/market/investors/kospi/005930/investors'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuCd": "KR7005930003",
        "isuSrtCd": "005930",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 534814,
                "askTrdval": 35819799,
                "bidTrdvol": 1365197,
                "bidTrdval": 91357237
            },
            {
                "invstCd": "02",
                "askTrdvol": 110469,
                "askTrdval": 7389240,
                "bidTrdvol": 53331,
                "bidTrdval": 3574395
            }
        ]
    }
}
```



## KOSPI 지수 투자자 마감정보 API  <a href="#api" id="api"></a>

* KOSPI 투자자 마감정보 (업종-투자자별 참고)
* 제공시간 : 전일,당일 15:40이후

{% swagger baseUrl="https://{APIGWAddr}/v3/market/investors/kospi" path="/investors" method="get" summary="/v3/market/investors/kospi/investors" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "15303000",
        "isuSrtCd": "K1",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 5230835,
                "askTrdval": 237317084,
                "bidTrdvol": 8907542,
                "bidTrdval": 451127644
            },
            {
                "invstCd": "02",
                "askTrdvol": 1573971,
                "askTrdval": 65330223,
                "bidTrdvol": 1279825,
                "bidTrdval": 60207485
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
'https://testoap.k-mydata.org/v3/market/investors/kospi/investors'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "15303000",
        "isuSrtCd": "K1",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 5230835,
                "askTrdval": 237317084,
                "bidTrdvol": 8907542,
                "bidTrdval": 451127644
            },
            {
                "invstCd": "02",
                "askTrdvol": 1573971,
                "askTrdval": 65330223,
                "bidTrdvol": 1279825,
                "bidTrdval": 60207485
            }
        ]
    }
}
```





