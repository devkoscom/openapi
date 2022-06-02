# 주식실시간B

주식시장(코스닥시장)의 종목 현재가, 체결 등 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**



## (시세표) KOSDAQ 주식 현재가 리스트 API

* 전종목 스냅샷 \[현재가,체결량,누적체결량,매수/매도1호가]
* 1회 조회 요청 시 전종목의 현재가(1초주기)를 리스트 형식으로 제공
  * 현재가 | 현재가, 누적거래량, 누적거래대금
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq" path="/multiquote/stocks/lists" method="get" summary="/v3/market/realtime/kosdaq/multiquote/stocks/lists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "163036",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "trdPrc": 305,
            "accTrdvol": 40047906,
            "accTrdval": 12839465539,
            "mktcap": 61604557275
        },
        {
            "isuSrtCd": "900270",
            "trdPrc": 478,
            "accTrdvol": 23830014,
            "accTrdval": 11860548776,
            "mktcap": 39590282124
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/multiquote/stocks/lists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "163036",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "trdPrc": 305,
            "accTrdvol": 40047906,
            "accTrdval": 12839465539,
            "mktcap": 61604557275
        },
        {
            "isuSrtCd": "900270",
            "trdPrc": 478,
            "accTrdvol": 23830014,
            "accTrdval": 11860548776,
            "mktcap": 39590282124
        }
    ]
}
```

## (시세표) KOSDAQ 주식 시장별 시고저종 리스트 API

* 전종목 스냅샷 \[현재가,시가,고가,저가]
* 1회 조회 요청 시 시고저종을 리스트 형식으로 제공
  * 시간외단일가 시고저종 | 시가, 고가, 저가, 종가
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq" path="/multiquote/stocks/ohlclists" method="get" summary="/v3/market/realtime/kosdaq/multiquote/stocks/ohlclists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "163217",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "opnprc": 330,
            "hgprc": 354,
            "lwprc": 303,
            "trdPrc": 305
        },
        {
            "isuSrtCd": "900270",
            "opnprc": 545,
            "hgprc": 546,
            "lwprc": 478,
            "trdPrc": 478
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/multiquote/stocks/ohlclists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "163217",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "opnprc": 330,
            "hgprc": 354,
            "lwprc": 303,
            "trdPrc": 305
        },
        {
            "isuSrtCd": "900270",
            "opnprc": 545,
            "hgprc": 546,
            "lwprc": 478,
            "trdPrc": 478
        }
    ]
}
```



## (시세표) KOSDAQ 주식 시장별 시간외단일가 시고저종 리스트 API

* 전종목 스냅샷 \[시간외 단일가 현재가,시가,고가,저가]
* 1회 조회 요청 시 시간외단일가 시고저종을 리스트 형식으로 제공
  * 시간외단일가 시고저종 | 시간외단일가 시가, 고가, 저가, 종가
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq" path="/multiquote/stocks/ahtohlclists" method="get" summary="/v3/market/realtime/kosdaq/multiquote/stocks/ahtohlclists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "163315",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "opnprc": 0,
            "hgprc": 304,
            "lwprc": 303,
            "trdPrc": 303
        },
        {
            "isuSrtCd": "900270",
            "opnprc": 0,
            "hgprc": 475,
            "lwprc": 471,
            "trdPrc": 475
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/multiquote/stocks/ahtohlclists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "163315",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "opnprc": 0,
            "hgprc": 304,
            "lwprc": 303,
            "trdPrc": 303
        },
        {
            "isuSrtCd": "900270",
            "opnprc": 0,
            "hgprc": 475,
            "lwprc": 471,
            "trdPrc": 475
        }
    ]
}
```



## (시세표) KOSDAQ 주식 호가/잔량 리스트 API

* 전종목 스냅샷 \[현재가,매수/매도1호가,매수/매도1잔량]
* 1회 조회 요청 시 KOSPI 주식 호가/잔량을 리스트 형식으로 제공
  * 호가/잔량 | 현재가,매수/매도1호가,매수/매도1잔량
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq" path="/multiquote/stocks/quotelists" method="get" summary="/v3/market/realtime/kosdaq/multiquote/stocks/quotelists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "163407",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "trdPrc": 305,
            "askStep1BstordPrc": 305,
            "askStep1BstordRqty": 11646,
            "bidStep1BstordPrc": 304,
            "bidStep1BstordRqty": 163933
        },
        {
            "isuSrtCd": "900270",
            "trdPrc": 478,
            "askStep1BstordPrc": 479,
            "askStep1BstordRqty": 1042,
            "bidStep1BstordPrc": 478,
            "bidStep1BstordRqty": 77159
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/multiquote/stocks/quotelists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "163407",
    "isuLists": [
        {
            "isuSrtCd": "900110",
            "trdPrc": 305,
            "askStep1BstordPrc": 305,
            "askStep1BstordRqty": 11646,
            "bidStep1BstordPrc": 304,
            "bidStep1BstordRqty": 163933
        },
        {
            "isuSrtCd": "900270",
            "trdPrc": 478,
            "askStep1BstordPrc": 479,
            "askStep1BstordRqty": 1042,
            "bidStep1BstordPrc": 478,
            "bidStep1BstordRqty": 77159
        }
    ]
}
```



## (시세표) KOSDAQ 주식 복수종목 현재가 API

* 복수종목(최대 20종목)에 대한 실시간 현재가 조회
* 현재가 실시간 조회를 최대 20개의 임의의 종목에 대해 일괄적으로 조회
  * 복수종목 리스트간 구분자는 쉼표(,) 임
  * 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq" path="/multiquote/stocks/price" method="get" summary="/v3/market/realtime/kosdaq/multiquote/stocks/price" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="isuCd" required="true" %}
ex) 900110,900270
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isulist": [
            {
                "trdPrc": 305,
                "cmpprevddTpCd": "5",
                "opnprc": 330,
                "hgprc": 354,
                "lwprc": 303,
                "accTrdvol": 40047906,
                "trdTm": 16301400,
                "trdvol": 11106,
                "accTrdval": 12839465539,
                "cmpprevddPrc": -9,
                "isuSrtCd": "900110",
                "bidordPrc_1": 304,
                "askordPrc_1": 305,
                "lstAskbidTpCd": 1
            },
            {
                "trdPrc": 478,
                "cmpprevddTpCd": "5",
                "opnprc": 545,
                "hgprc": 546,
                "lwprc": 478,
                "accTrdvol": 23830014,
                "trdTm": 16302500,
                "trdvol": 12756,
                "accTrdval": 11860548776,
                "cmpprevddPrc": -52,
                "isuSrtCd": "900270",
                "bidordPrc_1": 478,
                "askordPrc_1": 479,
                "lstAskbidTpCd": 2
            }
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```javascript
{
    "error": "서브마켓/코드가 정상적이지 않습니다."
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/multiquote/stocks/price?isuCd=900110,900270'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isulist": [
            {
                "trdPrc": 66700,
                "cmpprevddTpCd": "5",
                "opnprc": 66600,
                "hgprc": 67000,
                "lwprc": 66400,
                "accTrdvol": 13842589,
                "trdTm": 15482500,
                "trdvol": 3,
                "accTrdval": 922217136500,
                "cmpprevddPrc": -700,
                "isuSrtCd": "005930",
                "bidordPrc_1": 66600,
                "askordPrc_1": 66700,
                "lstAskbidTpCd": 1
            },
            {
                "trdPrc": 107000,
                "cmpprevddTpCd": "5",
                "opnprc": 106000,
                "hgprc": 107500,
                "lwprc": 106000,
                "accTrdvol": 3066412,
                "trdTm": 15481000,
                "trdvol": 1,
                "accTrdval": 327014746000,
                "cmpprevddPrc": -1000,
                "isuSrtCd": "000660",
                "bidordPrc_1": 106500,
                "askordPrc_1": 107000,
                "lstAskbidTpCd": 2
            }
        ]
    }
}
```



## (시세표) KOSDAQ주식 복수종목 호가잔량 API

* 복수종목(최대 20종목)에 대한 실시간 호가잔량 조회
* 호가잔량 실시간 조회를 최대 20개의 임의의 종목에 대해 일괄적으로 조회
  * 복수종목 리스트간 구분자는 쉼표(,) 임
  * 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq" path="/multiquote/stocks/orderbook" method="get" summary="/v3/market/realtime/kosdaq/multiquote/stocks/orderbook" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="isuCd" required="true" %}
ex) 900110,900270
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isulist": [
            {
                "askStep1BstordPrc": 305,
                "askStep2BstordPrc": 306,
                "askStep3BstordPrc": 307,
                "askStep4BstordPrc": 308,
                "askStep5BstordPrc": 309,
                "askStep6BstordPrc": 310,
                "askStep7BstordPrc": 311,
                "askStep8BstordPrc": 312,
                "askStep9BstordPrc": 313,
                "askStep10BstordPrc": 314,
                "askStep1BstordRqty": 11646,
                "askStep2BstordRqty": 10025,
                "askStep3BstordRqty": 105999,
                "askStep4BstordRqty": 53921,
                "askStep5BstordRqty": 31547,
                "askStep6BstordRqty": 53453,
                "askStep7BstordRqty": 16360,
                "askStep8BstordRqty": 28097,
                "askStep9BstordRqty": 45287,
                "askStep10BstordRqty": 109466,
                "bidStep1BstordPrc": 304,
                "bidStep2BstordPrc": 303,
                "bidStep3BstordPrc": 302,
                "bidStep4BstordPrc": 301,
                "bidStep5BstordPrc": 300,
                "bidStep6BstordPrc": 299,
                "bidStep7BstordPrc": 298,
                "bidStep8BstordPrc": 297,
                "bidStep9BstordPrc": 296,
                "bidStep10BstordPrc": 295,
                "bidStep1BstordRqty": 163933,
                "bidStep2BstordRqty": 275723,
                "bidStep3BstordRqty": 79545,
                "bidStep4BstordRqty": 35853,
                "bidStep5BstordRqty": 121944,
                "bidStep6BstordRqty": 91902,
                "bidStep7BstordRqty": 119084,
                "bidStep8BstordRqty": 69809,
                "bidStep9BstordRqty": 26081,
                "bidStep10BstordRqty": 28602,
                "askordTotRqty": 465801,
                "bidordTotRqty": 1012476,
                "pstoffhrAskTotOrdRqty": 0,
                "pstoffhrBidTotOrdRqty": 18692,
                "accTrdvol": 40047906,
                "deemTrdPrc": 305,
                "deemTrdvol": 10,
                "deemAccTrdvol": 308665,
                "isuSrtCd": "900110"
            },
            {
                "askStep1BstordPrc": 479,
                "askStep2BstordPrc": 480,
                "askStep3BstordPrc": 482,
                "askStep4BstordPrc": 483,
                "askStep5BstordPrc": 484,
                "askStep6BstordPrc": 485,
                "askStep7BstordPrc": 486,
                "askStep8BstordPrc": 487,
                "askStep9BstordPrc": 488,
                "askStep10BstordPrc": 489,
                "askStep1BstordRqty": 1042,
                "askStep2BstordRqty": 35242,
                "askStep3BstordRqty": 22535,
                "askStep4BstordRqty": 500,
                "askStep5BstordRqty": 21363,
                "askStep6BstordRqty": 27140,
                "askStep7BstordRqty": 26751,
                "askStep8BstordRqty": 6683,
                "askStep9BstordRqty": 4384,
                "askStep10BstordRqty": 29736,
                "bidStep1BstordPrc": 478,
                "bidStep2BstordPrc": 477,
                "bidStep3BstordPrc": 476,
                "bidStep4BstordPrc": 475,
                "bidStep5BstordPrc": 474,
                "bidStep6BstordPrc": 473,
                "bidStep7BstordPrc": 472,
                "bidStep8BstordPrc": 471,
                "bidStep9BstordPrc": 470,
                "bidStep10BstordPrc": 469,
                "bidStep1BstordRqty": 77159,
                "bidStep2BstordRqty": 33934,
                "bidStep3BstordRqty": 39440,
                "bidStep4BstordRqty": 29540,
                "bidStep5BstordRqty": 9109,
                "bidStep6BstordRqty": 14796,
                "bidStep7BstordRqty": 18391,
                "bidStep8BstordRqty": 5091,
                "bidStep9BstordRqty": 43783,
                "bidStep10BstordRqty": 5059,
                "askordTotRqty": 175376,
                "bidordTotRqty": 276302,
                "pstoffhrAskTotOrdRqty": 32579,
                "pstoffhrBidTotOrdRqty": 0,
                "accTrdvol": 23830014,
                "deemTrdPrc": 478,
                "deemTrdvol": -11593,
                "deemAccTrdvol": 184881,
                "isuSrtCd": "900270"
            }
        ]
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```javascript
{
    "error": "서브마켓/코드가 정상적이지 않습니다."
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/multiquote/stocks/orderbook?isuCd=900110,900270'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isulist": [
            {
                "askStep1BstordPrc": 305,
                "askStep2BstordPrc": 306,
                "askStep3BstordPrc": 307,
                "askStep4BstordPrc": 308,
                "askStep5BstordPrc": 309,
                "askStep6BstordPrc": 310,
                "askStep7BstordPrc": 311,
                "askStep8BstordPrc": 312,
                "askStep9BstordPrc": 313,
                "askStep10BstordPrc": 314,
                "askStep1BstordRqty": 11646,
                "askStep2BstordRqty": 10025,
                "askStep3BstordRqty": 105999,
                "askStep4BstordRqty": 53921,
                "askStep5BstordRqty": 31547,
                "askStep6BstordRqty": 53453,
                "askStep7BstordRqty": 16360,
                "askStep8BstordRqty": 28097,
                "askStep9BstordRqty": 45287,
                "askStep10BstordRqty": 109466,
                "bidStep1BstordPrc": 304,
                "bidStep2BstordPrc": 303,
                "bidStep3BstordPrc": 302,
                "bidStep4BstordPrc": 301,
                "bidStep5BstordPrc": 300,
                "bidStep6BstordPrc": 299,
                "bidStep7BstordPrc": 298,
                "bidStep8BstordPrc": 297,
                "bidStep9BstordPrc": 296,
                "bidStep10BstordPrc": 295,
                "bidStep1BstordRqty": 163933,
                "bidStep2BstordRqty": 275723,
                "bidStep3BstordRqty": 79545,
                "bidStep4BstordRqty": 35853,
                "bidStep5BstordRqty": 121944,
                "bidStep6BstordRqty": 91902,
                "bidStep7BstordRqty": 119084,
                "bidStep8BstordRqty": 69809,
                "bidStep9BstordRqty": 26081,
                "bidStep10BstordRqty": 28602,
                "askordTotRqty": 465801,
                "bidordTotRqty": 1012476,
                "pstoffhrAskTotOrdRqty": 0,
                "pstoffhrBidTotOrdRqty": 18692,
                "accTrdvol": 40047906,
                "deemTrdPrc": 305,
                "deemTrdvol": 10,
                "deemAccTrdvol": 308665,
                "isuSrtCd": "900110"
            },
            {
                "askStep1BstordPrc": 479,
                "askStep2BstordPrc": 480,
                "askStep3BstordPrc": 482,
                "askStep4BstordPrc": 483,
                "askStep5BstordPrc": 484,
                "askStep6BstordPrc": 485,
                "askStep7BstordPrc": 486,
                "askStep8BstordPrc": 487,
                "askStep9BstordPrc": 488,
                "askStep10BstordPrc": 489,
                "askStep1BstordRqty": 1042,
                "askStep2BstordRqty": 35242,
                "askStep3BstordRqty": 22535,
                "askStep4BstordRqty": 500,
                "askStep5BstordRqty": 21363,
                "askStep6BstordRqty": 27140,
                "askStep7BstordRqty": 26751,
                "askStep8BstordRqty": 6683,
                "askStep9BstordRqty": 4384,
                "askStep10BstordRqty": 29736,
                "bidStep1BstordPrc": 478,
                "bidStep2BstordPrc": 477,
                "bidStep3BstordPrc": 476,
                "bidStep4BstordPrc": 475,
                "bidStep5BstordPrc": 474,
                "bidStep6BstordPrc": 473,
                "bidStep7BstordPrc": 472,
                "bidStep8BstordPrc": 471,
                "bidStep9BstordPrc": 470,
                "bidStep10BstordPrc": 469,
                "bidStep1BstordRqty": 77159,
                "bidStep2BstordRqty": 33934,
                "bidStep3BstordRqty": 39440,
                "bidStep4BstordRqty": 29540,
                "bidStep5BstordRqty": 9109,
                "bidStep6BstordRqty": 14796,
                "bidStep7BstordRqty": 18391,
                "bidStep8BstordRqty": 5091,
                "bidStep9BstordRqty": 43783,
                "bidStep10BstordRqty": 5059,
                "askordTotRqty": 175376,
                "bidordTotRqty": 276302,
                "pstoffhrAskTotOrdRqty": 32579,
                "pstoffhrBidTotOrdRqty": 0,
                "accTrdvol": 23830014,
                "deemTrdPrc": 478,
                "deemTrdvol": -11593,
                "deemAccTrdvol": 184881,
                "isuSrtCd": "900270"
            }
        ]
    }
}
```



## KOSDAQ 주식종목 체결 API  <a href="#api" id="api"></a>

* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq/stocks" path="/{issuecode}/price" method="get" summary="/v3/market/realtime/kosdaq/stocks/{issuecode}/price" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)900110
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110",
        "trdPrc": 305,
        "cmpprevddTpCd": "5",
        "opnprc": 330,
        "hgprc": 354,
        "lwprc": 303,
        "accTrdvol": 40047906,
        "trdTm": 16301400,
        "trdvol": 11106,
        "accTrdval": 12839465539,
        "cmpprevddPrc": -9,
        "bidordPrc_1": 304,
        "askordPrc_1": 305,
        "lstAskbidTpCd": 1
    }
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}
```javascript
{
    "error": "서브마켓/코드가 정상적이지 않습니다."
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
| isuSrtCd      | string(9)  | 종목단축코드          | 예) KR7000660001 → 000660                             |
| cmpprevddTpCd | string(1)  | 전일대비구분코드        | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc  | number(11) | 전일대비가격          | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0                     |
| opnprc        | number(11) | 시가              | 단위:원                                                 |
| hgprc         | number(11) | 고가              | 단위:원                                                 |
| lwprc         | number(11) | 저가              | 단위:원                                                 |
| trdPrc        | number(11) | 체결가격            | 0                                                    |
| trdvol        | number(10) | 체결수량, 거래량       | 0                                                    |
| accTrdvol     | number(12) | 누적체결수량,누적거래량    | 단위:주                                                 |
| accTrdval     | number(22) | 누적거래대금          | 단위:원                                                 |
| lstAskbidTpCd | string(1)  | 최종매도매수구분코드      | 1:매도, 2:매수 (최종으로 들어온 호가의 매도매수구분값)                    |
| trdTm         | string(8)  | 체결시각,거래시각       | \*테이블 하단 참고                                          |
| askordPrc\_1  | number(11) | 매도호가가격\_1       | 단위:원 (체결+우선호가 발생시에만 전송)                              |
| bidordPrc\_1  | number(11) | 매수호가가격\_1       | 단위:원                                                 |

> `trdTm`: 체결시각,거래시각
>
> * HHMMSSmm 형태로 시간전송
>   * 정규장 개시전 또는 정규장 체결 발생 이전 : 0 &#x20;
>   *   장운영시그널, 대량체결 포함 &#x20;
>
>       ※ _장운영시그널_ &#x20;
>
>       정규장마감(15:00):31000000 /장종료시간외마감(15:30):41000000 /단일가마감(18:00):81000000 /일반Buy-in마감(18:00):91000007 /당일Buy-in마감(18:00):91000008 &#x20;
>
>       ※ _대량체결시_  &#x20;
>
>       장전대량매매체결:51000000 /장중대량매매체결:61000000 /장후대량매매체결:71000000

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/stocks/900110/price'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110",
        "trdPrc": 305,
        "cmpprevddTpCd": "5",
        "opnprc": 330,
        "hgprc": 354,
        "lwprc": 303,
        "accTrdvol": 40047906,
        "trdTm": 16301400,
        "trdvol": 11106,
        "accTrdval": 12839465539,
        "cmpprevddPrc": -9,
        "bidordPrc_1": 304,
        "askordPrc_1": 305,
        "lstAskbidTpCd": 1
    }
}
```



## KOSDAQ 주식 종목 호가잔량 (LP호가제외) API  <a href="#api" id="api"></a>

* 종목 호가잔량 (LP호가 제외)
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq/stocks" path="/{issuecode}/orderbook" method="get" summary="/v3/market/realtime/kosdaq/stocks/{issuecode}/orderbook" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)900110
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110",
        "askStep1BstordPrc": 305,
        "askStep2BstordPrc": 306,
        "askStep3BstordPrc": 307,
        "askStep4BstordPrc": 308,
        "askStep5BstordPrc": 309,
        "askStep6BstordPrc": 310,
        "askStep7BstordPrc": 311,
        "askStep8BstordPrc": 312,
        "askStep9BstordPrc": 313,
        "askStep10BstordPrc": 314,
        "askStep1BstordRqty": 11646,
        "askStep2BstordRqty": 10025,
        "askStep3BstordRqty": 105999,
        "askStep4BstordRqty": 53921,
        "askStep5BstordRqty": 31547,
        "askStep6BstordRqty": 53453,
        "askStep7BstordRqty": 16360,
        "askStep8BstordRqty": 28097,
        "askStep9BstordRqty": 45287,
        "askStep10BstordRqty": 109466,
        "bidStep1BstordPrc": 304,
        "bidStep2BstordPrc": 303,
        "bidStep3BstordPrc": 302,
        "bidStep4BstordPrc": 301,
        "bidStep5BstordPrc": 300,
        "bidStep6BstordPrc": 299,
        "bidStep7BstordPrc": 298,
        "bidStep8BstordPrc": 297,
        "bidStep9BstordPrc": 296,
        "bidStep10BstordPrc": 295,
        "bidStep1BstordRqty": 163933,
        "bidStep2BstordRqty": 275723,
        "bidStep3BstordRqty": 79545,
        "bidStep4BstordRqty": 35853,
        "bidStep5BstordRqty": 121944,
        "bidStep6BstordRqty": 91902,
        "bidStep7BstordRqty": 119084,
        "bidStep8BstordRqty": 69809,
        "bidStep9BstordRqty": 26081,
        "bidStep10BstordRqty": 28602,
        "askordTotRqty": 465801,
        "bidordTotRqty": 1012476,
        "pstoffhrAskTotOrdRqty": 0,
        "pstoffhrBidTotOrdRqty": 18692,
        "accTrdvol": 40056406,
        "deemTrdPrc": 305,
        "deemTrdvol": 10,
        "deemAccTrdvol": 308665
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

| **Name**              | **Type**   | **Description** |                           |
| --------------------- | ---------- | --------------- | ------------------------- |
| isuSrtCd              | string(9)  | 종목단축코드          | 예) KR7000660001 -> 000660 |
| accTrdvol             | number(12) | 누적체결수량,누적거래량    | 단위: 주                     |
| askStep1BstordPrc     | number(11) | 매도1단계우선호가가격     |                           |
| bidStep1BstordPrc     | number(11) | 매수1단계우선호가가격     |                           |
| askStep1BstordRqty    | number(12) | 매도1단계우선호가잔량     |                           |
| bidStep1BstordRqty    | number(12) | 매수1단계우선호가잔량     |                           |
| askStep2BstordPrc     | number(11) | 매도2단계우선호가가격     |                           |
| bidStep2BstordPrc     | number(11) | 매수2단계우선호가가격     |                           |
| askStep2BstordRqty    | number(12) | 매도2단계우선호가잔량     |                           |
| bidStep2BstordRqty    | number(12) | 매수2단계우선호가잔량     |                           |
| askStep3BstordPrc     | number(11) | 매도3단계우선호가가격     |                           |
| bidStep3BstordPrc     | number(11) | 매수3단계우선호가가격     |                           |
| askStep3BstordRqty    | number(12) | 매도3단계우선호가잔량     |                           |
| bidStep3BstordRqty    | number(12) | 매수3단계우선호가잔량     |                           |
| askStep4BstordPrc     | number(11) | 매도4단계우선호가가격     |                           |
| bidStep4BstordPrc     | number(11) | 매수4단계우선호가가격     |                           |
| askStep4BstordRqty    | number(12) | 매도4단계우선호가잔량     |                           |
| bidStep4BstordRqty    | number(12) | 매수4단계우선호가잔량     |                           |
| askStep5BstordPrc     | number(11) | 매도5단계우선호가가격     |                           |
| bidStep5BstordPrc     | number(11) | 매수5단계우선호가가격     |                           |
| askStep5BstordRqty    | number(12) | 매도5단계우선호가잔량     |                           |
| bidStep5BstordRqty    | number(12) | 매수5단계우선호가잔량     |                           |
| askStep6BstordPrc     | number(11) | 매도6단계우선호가가격     |                           |
| bidStep6BstordPrc     | number(11) | 매수6단계우선호가가격     |                           |
| askStep6BstordRqty    | number(12) | 매도6단계우선호가잔량     |                           |
| bidStep6BstordRqty    | number(12) | 매수6단계우선호가잔량     |                           |
| askStep7BstordPrc     | number(11) | 매도7단계우선호가가격     |                           |
| bidStep7BstordPrc     | number(11) | 매수7단계우선호가가격     |                           |
| askStep7BstordRqty    | number(12) | 매도7단계우선호가잔량     |                           |
| bidStep7BstordRqty    | number(12) | 매수7단계우선호가잔량     |                           |
| askStep8BstordPrc     | number(11) | 매도8단계우선호가가격     |                           |
| bidStep8BstordPrc     | number(11) | 매수8단계우선호가가격     |                           |
| askStep8BstordRqty    | number(12) | 매도8단계우선호가잔량     |                           |
| bidStep8BstordRqty    | number(12) | 매수8단계우선호가잔량     |                           |
| askStep9BstordPrc     | number(11) | 매도9단계우선호가가격     |                           |
| bidStep9BstordPrc     | number(11) | 매수9단계우선호가가격     |                           |
| askStep9BstordRqty    | number(12) | 매도9단계우선호가잔량     |                           |
| bidStep9BstordRqty    | number(12) | 매수9단계우선호가잔량     |                           |
| askStep10BstordPrc    | number(11) | 매도10단계우선호가가격    |                           |
| bidStep10BstordPrc    | number(11) | 매수10단계우선호가가격    |                           |
| askStep10BstordRqty   | number(12) | 매도10단계우선호가잔량    |                           |
| bidStep10BstordRqty   | number(12) | 매수10단계우선호가잔량    |                           |
| askordTotRqty         | number(12) | 매도호가총잔량         |                           |
| bidordTotRqty         | number(12) | 매수호가총잔량         |                           |
| pstoffhrAskTotOrdRqty | number(15) | 장종료후시간외매도총호가잔량  |                           |
| pstoffhrBidTotOrdRqty | number(15) | 장종료후시간외매수총호가잔량  |                           |
| deemTrdPrc            | number(11) | 예상체결가격          |                           |
| deemTrdvol            | number(12) | 예상체결수량          |                           |
| deemAccTrdvol         | number(12) | 예상누적체결수량        |                           |

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/stocks/900110/orderbook'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110",
        "askStep1BstordPrc": 305,
        "askStep2BstordPrc": 306,
        "askStep3BstordPrc": 307,
        "askStep4BstordPrc": 308,
        "askStep5BstordPrc": 309,
        "askStep6BstordPrc": 310,
        "askStep7BstordPrc": 311,
        "askStep8BstordPrc": 312,
        "askStep9BstordPrc": 313,
        "askStep10BstordPrc": 314,
        "askStep1BstordRqty": 11646,
        "askStep2BstordRqty": 10025,
        "askStep3BstordRqty": 105999,
        "askStep4BstordRqty": 53921,
        "askStep5BstordRqty": 31547,
        "askStep6BstordRqty": 53453,
        "askStep7BstordRqty": 16360,
        "askStep8BstordRqty": 28097,
        "askStep9BstordRqty": 45287,
        "askStep10BstordRqty": 109466,
        "bidStep1BstordPrc": 304,
        "bidStep2BstordPrc": 303,
        "bidStep3BstordPrc": 302,
        "bidStep4BstordPrc": 301,
        "bidStep5BstordPrc": 300,
        "bidStep6BstordPrc": 299,
        "bidStep7BstordPrc": 298,
        "bidStep8BstordPrc": 297,
        "bidStep9BstordPrc": 296,
        "bidStep10BstordPrc": 295,
        "bidStep1BstordRqty": 163933,
        "bidStep2BstordRqty": 275723,
        "bidStep3BstordRqty": 79545,
        "bidStep4BstordRqty": 35853,
        "bidStep5BstordRqty": 121944,
        "bidStep6BstordRqty": 91902,
        "bidStep7BstordRqty": 119084,
        "bidStep8BstordRqty": 69809,
        "bidStep9BstordRqty": 26081,
        "bidStep10BstordRqty": 28602,
        "askordTotRqty": 465801,
        "bidordTotRqty": 1012476,
        "pstoffhrAskTotOrdRqty": 0,
        "pstoffhrBidTotOrdRqty": 18692,
        "accTrdvol": 40056406,
        "deemTrdPrc": 305,
        "deemTrdvol": 10,
        "deemAccTrdvol": 308665
    }
}
```

## KOSDAQ 주식 종목 일중 API  <a href="#api" id="api"></a>

* 종목 일중 데이터 제공 \[10초, 1분, 10분단위 시/고/저/종]
* 최대 100건 까지만 조회 가능
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq/stocks" path="/{issuecode}/intraday" method="get" summary="/v3/market/realtime/kosdaq/stocks/{issuecode}/intraday" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)900110
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inddCycleTpCd" required="true" %}
일중 전송주기 구분코드 (10:10초, 60:1분, 600:10분)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" required="false" %}
조회시작일자 YYYYMMSS
{% endswagger-parameter %}

{% swagger-parameter in="query" name="strtTm" required="true" type="String" %}
개시시각,시작시각 HHMM
{% endswagger-parameter %}

{% swagger-parameter in="query" name="endTm" required="true" type="String" %}
종료시각 HHMM
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110",
        "hisLists": [
            {
                "inddTm": "10000000",
                "inddOpnprc": 315,
                "inddHgprc": 318,
                "inddLwprc": 314,
                "inddClsprc": 317,
                "inddTrdvol": 285329,
                "inddTrdval": 90086921,
                "inddAccTrdvol": 7205798,
                "inddAccTrdval": 2308304032
            },
            {
                "inddTm": "9500000",
                "inddOpnprc": 315,
                "inddHgprc": 317,
                "inddLwprc": 314,
                "inddClsprc": 315,
                "inddTrdvol": 434290,
                "inddTrdval": 136779297,
                "inddAccTrdvol": 6920469,
                "inddAccTrdval": 2218217111
            },
            {
                "inddTm": "9400000",
                "inddOpnprc": 321,
                "inddHgprc": 322,
                "inddLwprc": 313,
                "inddClsprc": 315,
                "inddTrdvol": 1095281,
                "inddTrdval": 346980725,
                "inddAccTrdvol": 6486179,
                "inddAccTrdval": 2081437814
            },
            {
                "inddTm": "9300000",
                "inddOpnprc": 320,
                "inddHgprc": 325,
                "inddLwprc": 320,
                "inddClsprc": 322,
                "inddTrdvol": 1329438,
                "inddTrdval": 428225267,
                "inddAccTrdvol": 5390898,
                "inddAccTrdval": 1734457089
            },
            {
                "inddTm": "9200000",
                "inddOpnprc": 320,
                "inddHgprc": 322,
                "inddLwprc": 316,
                "inddClsprc": 319,
                "inddTrdvol": 501757,
                "inddTrdval": 160220659,
                "inddAccTrdvol": 4061460,
                "inddAccTrdval": 1306231822
            },
            {
                "inddTm": "9100000",
                "inddOpnprc": 317,
                "inddHgprc": 330,
                "inddLwprc": 311,
                "inddClsprc": 322,
                "inddTrdvol": 3559703,
                "inddTrdval": 1146011163,
                "inddAccTrdvol": 3559703,
                "inddAccTrdval": 1146011163
            }
        ]
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

| **Name**      | **Type**   | **Description** |                             |
| ------------- | ---------- | --------------- | --------------------------- |
| isuSrtCd      | String(9)  | 종목단축코드          |                             |
| isuNm         | String(80) | 종목명             |                             |
| hisLists      | Array(4)   | 과거리스트           |                             |
| inddTm        | string(8)  | 일중시간            | HH:MM:SS                    |
| inddOpnprc    | number(11) | 일중시가            | 일중데이타(10초, 1분, 10분)         |
| inddHgprc     | number(11) | 일중고가            | 일중데이타(10초, 1분, 10분)         |
| inddLwprc     | number(11) | 일중저가            | 일중데이타(10초, 1분, 10분)         |
| inddClsprc    | number(11) | 일중종가            | 일중데이타(10초, 1분, 10분)         |
| inddTrdvol    | number(11) | 일중거래량           | 일중데이타(10초, 1분, 10분)         |
| inddTrdval    | number(11) | 일중거래대금          | 일중데이타(10초, 1분, 10분) 구간 거래대금 |
| inddAccTrdvol | number(11) | 일중누적거래량         | 일중 누적거래량                    |
| inddAccTrdval | number(11) | 일중누적대금          | 일중 누적거래대금                   |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/stocks/900110/intraday?inddCycleTpCd=600&inqStrtDd=20220501&strtTm=0900&endTm=1500'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110",
        "hisLists": [
            {
                "inddTm": "10000000",
                "inddOpnprc": 315,
                "inddHgprc": 318,
                "inddLwprc": 314,
                "inddClsprc": 317,
                "inddTrdvol": 285329,
                "inddTrdval": 90086921,
                "inddAccTrdvol": 7205798,
                "inddAccTrdval": 2308304032
            },
            {
                "inddTm": "9500000",
                "inddOpnprc": 315,
                "inddHgprc": 317,
                "inddLwprc": 314,
                "inddClsprc": 315,
                "inddTrdvol": 434290,
                "inddTrdval": 136779297,
                "inddAccTrdvol": 6920469,
                "inddAccTrdval": 2218217111
            },
            {
                "inddTm": "9400000",
                "inddOpnprc": 321,
                "inddHgprc": 322,
                "inddLwprc": 313,
                "inddClsprc": 315,
                "inddTrdvol": 1095281,
                "inddTrdval": 346980725,
                "inddAccTrdvol": 6486179,
                "inddAccTrdval": 2081437814
            },
            {
                "inddTm": "9300000",
                "inddOpnprc": 320,
                "inddHgprc": 325,
                "inddLwprc": 320,
                "inddClsprc": 322,
                "inddTrdvol": 1329438,
                "inddTrdval": 428225267,
                "inddAccTrdvol": 5390898,
                "inddAccTrdval": 1734457089
            },
            {
                "inddTm": "9200000",
                "inddOpnprc": 320,
                "inddHgprc": 322,
                "inddLwprc": 316,
                "inddClsprc": 319,
                "inddTrdvol": 501757,
                "inddTrdval": 160220659,
                "inddAccTrdvol": 4061460,
                "inddAccTrdval": 1306231822
            },
            {
                "inddTm": "9100000",
                "inddOpnprc": 317,
                "inddHgprc": 330,
                "inddLwprc": 311,
                "inddClsprc": 322,
                "inddTrdvol": 3559703,
                "inddTrdval": 1146011163,
                "inddAccTrdvol": 3559703,
                "inddAccTrdval": 1146011163
            }
        ]
    }
}
```



## KOSDAQ 주식 거래상위 회원사 정보 API  <a href="#api" id="api"></a>

* 종목 매수/매도 상위 5개 회원사 정보
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kosdaq/stocks" path="/{issuecode}/traderanking" method="get" summary="/v3/market/realtime/kosdaq/stocks/{issuecode}/traderanking" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)900110
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110*003",
        "askTrdVolMbr1": 10929239,
        "askTrdVolMbr2": 4989860,
        "askTrdVolMbr3": 4747453,
        "askTrdVolMbr4": 4509065,
        "askTrdVolMbr5": 4229361,
        "askTrdAmtMbr1": 3519606807,
        "askTrdAmtMbr2": 1601052862,
        "askTrdAmtMbr3": 1528462544,
        "askTrdAmtMbr4": 1435967463,
        "askTrdAmtMbr5": 1344186074,
        "askTrdWtMbr1": 27.42,
        "askTrdWtMbr2": 12.52,
        "askTrdWtMbr3": 11.91,
        "askTrdWtMbr4": 11.31,
        "askTrdWtMbr5": 10.61,
        "bidTrdVolMbr1": 10711479,
        "bidTrdVolMbr2": 5739910,
        "bidTrdVolMbr3": 5189784,
        "bidTrdVolMbr4": 3851073,
        "bidTrdVolMbr5": 3557160,
        "bidTrdAmtMbr1": 3445914869,
        "bidTrdAmtMbr2": 1835300257,
        "bidTrdAmtMbr3": 1665147334,
        "bidTrdAmtMbr4": 1232121197,
        "bidTrdAmtMbr5": 1147469775,
        "bidTrdWtMbr1": 26.88,
        "bidTrdWtMbr2": 14.4,
        "bidTrdWtMbr3": 13.02,
        "bidTrdWtMbr4": 9.66,
        "bidTrdWtMbr5": 8.93,
        "bidTrdPrcMbr1": 322,
        "bidTrdPrcMbr2": 320,
        "bidTrdPrcMbr3": 321,
        "bidTrdPrcMbr4": 320,
        "bidTrdPrcMbr5": 323,
        "askTrdPrcMbr1": 322,
        "askTrdPrcMbr2": 321,
        "askTrdPrcMbr3": 322,
        "askTrdPrcMbr4": 318,
        "askTrdPrcMbr5": 318,
        "bidTrdMbr1": "키움증권",
        "bidTrdMbr2": "KB증권",
        "bidTrdMbr3": "NH투자증권",
        "bidTrdMbr4": "한국증권",
        "bidTrdMbr5": "미래에셋증권",
        "askTrdMbr1": "키움증권",
        "askTrdMbr2": "한국증권",
        "askTrdMbr3": "NH투자증권",
        "askTrdMbr4": "KB증권",
        "askTrdMbr5": "미래에셋증권"
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

| **Name**      | **Type**   | **Description** |                                   |
| ------------- | ---------- | --------------- | --------------------------------- |
| bidTrdMbr1    | string(64) | 매수상위회원명1        | 매수랭킹 TOP5 1위 회원사 한글명              |
| bidTrdMbr2    | string(64) | 매수상위회원명2        | 매수랭킹 TOP5 2위 회원사 한글명              |
| bidTrdMbr3    | string(64) | 매수상위회원명3        | 매수랭킹 TOP5 3위 회원사 한글명              |
| bidTrdMbr4    | string(64) | 매수상위회원명4        | 매수랭킹 TOP5 4위 회원사 한글명              |
| bidTrdMbr5    | string(64) | 매수상위회원명5        | 매수랭킹 TOP5 5위 회원사 한글명              |
| askTrdMbr1    | string(64) | 매도상위회원명1        | 매도랭킹 TOP5 1위 회원사 한글명              |
| askTrdMbr2    | string(64) | 매도상위회원명2        | 매도랭킹 TOP5 2위 회원사 한글명              |
| askTrdMbr3    | string(64) | 매도상위회원명3        | 매도랭킹 TOP5 3위 회원사 한글명              |
| askTrdMbr4    | string(64) | 매도상위회원명4        | 매도랭킹 TOP5 4위 회원사 한글명              |
| askTrdMbr5    | string(64) | 매도상위회원명5        | 매도랭킹 TOP5 5위 회원사 한글명              |
| bidTrdVolMbr1 | number(11) | 매수상위거래량 회원1     | 매수랭킹 TOP5 1위 회원사 거래량              |
| bidTrdVolMbr2 | number(11) | 매수상위거래량 회원2     |                                   |
| bidTrdVolMbr3 | number(11) | 매수상위거래량 회원3     |                                   |
| bidTrdVolMbr4 | number(11) | 매수상위거래량 회원4     |                                   |
| bidTrdVolMbr5 | number(11) | 매수상위거래량 회원5     |                                   |
| askTrdVolMbr1 | number(11) | 매도상위거래량 회원1     | 매도랭킹 TOP5 1위 회원사 거래량              |
| askTrdVolMbr2 | number(11) | 매도상위거래량 회원2     |                                   |
| askTrdVolMbr3 | number(11) | 매도상위거래량 회원3     |                                   |
| askTrdVolMbr4 | number(11) | 매도상위거래량 회원4     |                                   |
| askTrdVolMbr5 | number(11) | 매도상위거래량 회원5     |                                   |
| bidTrdAmtMbr1 | number(11) | 매수상위거래금액 회원1    | 매수랭킹 TOP5 1위 회원사 거래금액             |
| bidTrdAmtMbr2 | number(11) | 매수상위거래금액 회원2    |                                   |
| bidTrdAmtMbr3 | number(11) | 매수상위거래금액 회원3    |                                   |
| bidTrdAmtMbr4 | number(11) | 매수상위거래금액 회원4    |                                   |
| bidTrdAmtMbr5 | number(11) | 매수상위거래금액 회원5    |                                   |
| askTrdAmtMbr1 | number(11) | 매도상위거래금액 회원1    | 매도랭킹 TOP5 1위 회원사 거래금액             |
| askTrdAmtMbr2 | number(11) | 매도상위거래금액 회원2    |                                   |
| askTrdAmtMbr3 | number(11) | 매도상위거래금액 회원3    |                                   |
| askTrdAmtMbr4 | number(11) | 매도상위거래금액 회원4    |                                   |
| askTrdAmtMbr5 | number(11) | 매도상위거래금액 회원5    |                                   |
| bidTrdPrcMbr1 | number(11) | 매수상위거래단가 회원1    | 매수랭킹 TOP5 1위 회원사 거래단가             |
| bidTrdPrcMbr2 | number(11) | 매수상위거래단가 회원2    |                                   |
| bidTrdPrcMbr3 | number(11) | 매수상위거래단가 회원3    |                                   |
| bidTrdPrcMbr4 | number(11) | 매수상위거래단가 회원4    |                                   |
| bidTrdPrcMbr5 | number(11) | 매수상위거래단가 회원5    |                                   |
| askTrdPrcMbr1 | number(11) | 매도상위거래단가 회원1    | 매도랭킹 TOP5 1위 회원사 거래단가             |
| askTrdPrcMbr2 | number(11) | 매도상위거래단가 회원2    |                                   |
| askTrdPrcMbr3 | number(11) | 매도상위거래단가 회원3    |                                   |
| askTrdPrcMbr4 | number(11) | 매도상위거래단가 회원4    |                                   |
| askTrdPrcMbr5 | number(11) | 매도상위거래단가 회원5    |                                   |
| bidTrdWtMbr1  | number(5)  | 매수상위거래비중 회원1    | 매수랭킹 TOP5 1위 회원사 거래비중 (백분율, X100) |
| bidTrdWtMbr2  | number(5)  | 매수상위거래비중 회원2    |                                   |
| bidTrdWtMbr3  | number(5)  | 매수상위거래비중 회원3    |                                   |
| bidTrdWtMbr4  | number(5)  | 매수상위거래비중 회원4    |                                   |
| bidTrdWtMbr5  | number(5)  | 매수상위거래비중 회원5    |                                   |
| askTrdWtMbr1  | number(5)  | 매도상위거래비중 회원1    | 매도랭킹 TOP5 1위 회원사 거래비중 (백분율, X100) |
| askTrdWtMbr2  | number(5)  | 매도상위거래비중 회원2    |                                   |
| askTrdWtMbr3  | number(5)  | 매도상위거래비중 회원3    |                                   |
| askTrdWtMbr4  | number(5)  | 매도상위거래비중 회원4    |                                   |
| askTrdWtMbr5  | number(5)  | 매도상위거래비중 회원5    |                                   |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kosdaq/stocks/900110/traderanking'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "900110*003",
        "askTrdVolMbr1": 10929239,
        "askTrdVolMbr2": 4989860,
        "askTrdVolMbr3": 4747453,
        "askTrdVolMbr4": 4509065,
        "askTrdVolMbr5": 4229361,
        "askTrdAmtMbr1": 3519606807,
        "askTrdAmtMbr2": 1601052862,
        "askTrdAmtMbr3": 1528462544,
        "askTrdAmtMbr4": 1435967463,
        "askTrdAmtMbr5": 1344186074,
        "askTrdWtMbr1": 27.42,
        "askTrdWtMbr2": 12.52,
        "askTrdWtMbr3": 11.91,
        "askTrdWtMbr4": 11.31,
        "askTrdWtMbr5": 10.61,
        "bidTrdVolMbr1": 10711479,
        "bidTrdVolMbr2": 5739910,
        "bidTrdVolMbr3": 5189784,
        "bidTrdVolMbr4": 3851073,
        "bidTrdVolMbr5": 3557160,
        "bidTrdAmtMbr1": 3445914869,
        "bidTrdAmtMbr2": 1835300257,
        "bidTrdAmtMbr3": 1665147334,
        "bidTrdAmtMbr4": 1232121197,
        "bidTrdAmtMbr5": 1147469775,
        "bidTrdWtMbr1": 26.88,
        "bidTrdWtMbr2": 14.4,
        "bidTrdWtMbr3": 13.02,
        "bidTrdWtMbr4": 9.66,
        "bidTrdWtMbr5": 8.93,
        "bidTrdPrcMbr1": 322,
        "bidTrdPrcMbr2": 320,
        "bidTrdPrcMbr3": 321,
        "bidTrdPrcMbr4": 320,
        "bidTrdPrcMbr5": 323,
        "askTrdPrcMbr1": 322,
        "askTrdPrcMbr2": 321,
        "askTrdPrcMbr3": 322,
        "askTrdPrcMbr4": 318,
        "askTrdPrcMbr5": 318,
        "bidTrdMbr1": "키움증권",
        "bidTrdMbr2": "KB증권",
        "bidTrdMbr3": "NH투자증권",
        "bidTrdMbr4": "한국증권",
        "bidTrdMbr5": "미래에셋증권",
        "askTrdMbr1": "키움증권",
        "askTrdMbr2": "한국증권",
        "askTrdMbr3": "NH투자증권",
        "askTrdMbr4": "KB증권",
        "askTrdMbr5": "미래에셋증권"
    }
}
```



