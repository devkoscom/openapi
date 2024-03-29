# 주식실시간A

주식시장(유가증권)의 종목 현재가, 체결 등 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**



## (시세표) KOSPI 주식 현재가 리스트 API

* 전종목 스냅샷 \[현재가,체결량,누적체결량,매수/매도1호가]
* 1회 조회 요청 시 전종목의 현재가(1초주기)를 리스트 형식으로 제공
  * 현재가 | 현재가, 누적거래량, 누적거래대금
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi" path="/multiquote/stocks/lists" method="get" summary="/v3/market/realtime/kospi/multiquote/stocks/lists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "153039",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "trdPrc": 11900,
            "accTrdvol": 87204,
            "accTrdval": 1037307300,
            "mktcap": 332384493000
        },
        {
            "isuSrtCd": "000040",
            "trdPrc": 776,
            "accTrdvol": 172934,
            "accTrdval": 133737054,
            "mktcap": 74602801656
        },
        {
            "isuSrtCd": "000050",
            "trdPrc": 14900,
            "accTrdvol": 16017,
            "accTrdval": 240530100,
            "mktcap": 408487523000
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/multiquote/stocks/lists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "153039",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "trdPrc": 11900,
            "accTrdvol": 87204,
            "accTrdval": 1037307300,
            "mktcap": 332384493000
        },
        {
            "isuSrtCd": "000040",
            "trdPrc": 776,
            "accTrdvol": 172934,
            "accTrdval": 133737054,
            "mktcap": 74602801656
        },
        {
            "isuSrtCd": "000050",
            "trdPrc": 14900,
            "accTrdvol": 16017,
            "accTrdval": 240530100,
            "mktcap": 408487523000
        }
    ]
 }   
```

## (시세표) KOSPI 주식 시장별 시고저종 리스트 API

* 전종목 스냅샷 \[현재가,시가,고가,저가]
* 1회 조회 요청 시 시고저종을 리스트 형식으로 제공
  * 시간외단일가 시고저종 | 시가, 고가, 저가, 종가
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi" path="/multiquote/stocks/ohlclists" method="get" summary="/v3/market/realtime/kospi/multiquote/stocks/ohlclists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "153344",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "opnprc": 11850,
            "hgprc": 12000,
            "lwprc": 11850,
            "trdPrc": 11900
        },
        {
            "isuSrtCd": "000040",
            "opnprc": 769,
            "hgprc": 777,
            "lwprc": 769,
            "trdPrc": 776
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/multiquote/stocks/ohlclists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "153344",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "opnprc": 11850,
            "hgprc": 12000,
            "lwprc": 11850,
            "trdPrc": 11900
        },
        {
            "isuSrtCd": "000040",
            "opnprc": 769,
            "hgprc": 777,
            "lwprc": 769,
            "trdPrc": 776
        }
    ]
}       
```



## (시세표) KOSPI 주식 시장별 시간외단일가 시고저종 리스트 API

* 전종목 스냅샷 \[시간외 단일가 현재가,시가,고가,저가]
* 1회 조회 요청 시 시간외단일가 시고저종을 리스트 형식으로 제공
  * 시간외단일가 시고저종 | 시간외단일가 시가, 고가, 저가, 종가
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi" path="/multiquote/stocks/ahtohlclists" method="get" summary="/v3/market/realtime/kospi/multiquote/stocks/ahtohlclists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "154013",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "opnprc": 0,
            "hgprc": 0,
            "lwprc": 0,
            "trdPrc": 11900
        },
        {
            "isuSrtCd": "000040",
            "opnprc": 0,
            "hgprc": 0,
            "lwprc": 0,
            "trdPrc": 776
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/multiquote/stocks/ahtohlclists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "154013",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "opnprc": 0,
            "hgprc": 0,
            "lwprc": 0,
            "trdPrc": 11900
        },
        {
            "isuSrtCd": "000040",
            "opnprc": 0,
            "hgprc": 0,
            "lwprc": 0,
            "trdPrc": 776
        }
    ]
}
```



## (시세표) KOSPI 주식 호가/잔량 리스트 API

* 전종목 스냅샷 \[현재가,매수/매도1호가,매수/매도1잔량]
* 1회 조회 요청 시 KOSPI 주식 호가/잔량을 리스트 형식으로 제공
  * 호가/잔량 | 현재가,매수/매도1호가,매수/매도1잔량
  * 제공시간 : 1초간격

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi" path="/multiquote/stocks/quotelists" method="get" summary="/v3/market/realtime/kospi/multiquote/stocks/quotelists" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "trdTm": "154342",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "trdPrc": 11900,
            "askStep1BstordPrc": 11950,
            "askStep1BstordRqty": 1188,
            "bidStep1BstordPrc": 11900,
            "bidStep1BstordRqty": 7641
        },
        {
            "isuSrtCd": "000040",
            "trdPrc": 776,
            "askStep1BstordPrc": 776,
            "askStep1BstordRqty": 1348,
            "bidStep1BstordPrc": 775,
            "bidStep1BstordRqty": 86
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/multiquote/stocks/quotelists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "trdTm": "154342",
    "isuLists": [
        {
            "isuSrtCd": "000020",
            "trdPrc": 11900,
            "askStep1BstordPrc": 11950,
            "askStep1BstordRqty": 1188,
            "bidStep1BstordPrc": 11900,
            "bidStep1BstordRqty": 7641
        },
        {
            "isuSrtCd": "000040",
            "trdPrc": 776,
            "askStep1BstordPrc": 776,
            "askStep1BstordRqty": 1348,
            "bidStep1BstordPrc": 775,
            "bidStep1BstordRqty": 86
        }
    ]
}
```



## (시세표) KOSPI 주식 복수종목 현재가 API

* 복수종목(최대 20종목)에 대한 실시간 현재가 조회
* 현재가 실시간 조회를 최대 20개의 임의의 종목에 대해 일괄적으로 조회
  * 복수종목 리스트간 구분자는 쉼표(,) 임
  * 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi" path="/multiquote/stocks/price" method="get" summary="/v3/market/realtime/kospi/multiquote/stocks/price" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="isuCd" required="true" %}
ex) 005930,000660
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kospi/multiquote/stocks/price?isuCd=005930,000660'
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



## (시세표) KOSPI 주식 복수종목 호가잔량 API

* 복수종목(최대 20종목)에 대한 실시간 호가잔량 조회
* 호가잔량 실시간 조회를 최대 20개의 임의의 종목에 대해 일괄적으로 조회
  * 복수종목 리스트간 구분자는 쉼표(,) 임
  * 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi" path="/multiquote/stocks/orderbook" method="get" summary="/v3/market/realtime/kospi/multiquote/stocks/orderbook" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="isuCd" required="true" %}
ex) 005930,000660
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isulist": [
            {
                "askStep1BstordPrc": 66700,
                "askStep2BstordPrc": 66800,
                "askStep3BstordPrc": 66900,
                "askStep4BstordPrc": 67000,
                "askStep5BstordPrc": 67100,
                "askStep6BstordPrc": 67200,
                "askStep7BstordPrc": 67300,
                "askStep8BstordPrc": 67400,
                "askStep9BstordPrc": 67500,
                "askStep10BstordPrc": 67600,
                "askStep1BstordRqty": 10663,
                "askStep2BstordRqty": 241244,
                "askStep3BstordRqty": 152601,
                "askStep4BstordRqty": 116059,
                "askStep5BstordRqty": 32390,
                "askStep6BstordRqty": 22328,
                "askStep7BstordRqty": 20267,
                "askStep8BstordRqty": 41831,
                "askStep9BstordRqty": 46067,
                "askStep10BstordRqty": 25594,
                "bidStep1BstordPrc": 66600,
                "bidStep2BstordPrc": 66500,
                "bidStep3BstordPrc": 66400,
                "bidStep4BstordPrc": 66300,
                "bidStep5BstordPrc": 66200,
                "bidStep6BstordPrc": 66100,
                "bidStep7BstordPrc": 66000,
                "bidStep8BstordPrc": 65900,
                "bidStep9BstordPrc": 65800,
                "bidStep10BstordPrc": 65700,
                "bidStep1BstordRqty": 73314,
                "bidStep2BstordRqty": 72871,
                "bidStep3BstordRqty": 419704,
                "bidStep4BstordRqty": 282534,
                "bidStep5BstordRqty": 209295,
                "bidStep6BstordRqty": 198780,
                "bidStep7BstordRqty": 405176,
                "bidStep8BstordRqty": 65606,
                "bidStep9BstordRqty": 73575,
                "bidStep10BstordRqty": 46276,
                "askordTotRqty": 709044,
                "bidordTotRqty": 1847131,
                "pstoffhrAskTotOrdRqty": 0,
                "pstoffhrBidTotOrdRqty": 3661,
                "accTrdvol": 13842806,
                "deemTrdPrc": 66700,
                "deemTrdvol": 1,
                "deemAccTrdvol": 1194589,
                "isuSrtCd": "005930"
            },
            {
                "askStep1BstordPrc": 107000,
                "askStep2BstordPrc": 107500,
                "askStep3BstordPrc": 108000,
                "askStep4BstordPrc": 108500,
                "askStep5BstordPrc": 109000,
                "askStep6BstordPrc": 109500,
                "askStep7BstordPrc": 110000,
                "askStep8BstordPrc": 110500,
                "askStep9BstordPrc": 111000,
                "askStep10BstordPrc": 111500,
                "askStep1BstordRqty": 2615,
                "askStep2BstordRqty": 82113,
                "askStep3BstordRqty": 66430,
                "askStep4BstordRqty": 56091,
                "askStep5BstordRqty": 47491,
                "askStep6BstordRqty": 39123,
                "askStep7BstordRqty": 66341,
                "askStep8BstordRqty": 24777,
                "askStep9BstordRqty": 27659,
                "askStep10BstordRqty": 29438,
                "bidStep1BstordPrc": 106500,
                "bidStep2BstordPrc": 106000,
                "bidStep3BstordPrc": 105500,
                "bidStep4BstordPrc": 105000,
                "bidStep5BstordPrc": 104500,
                "bidStep6BstordPrc": 104000,
                "bidStep7BstordPrc": 103500,
                "bidStep8BstordPrc": 103000,
                "bidStep9BstordPrc": 102500,
                "bidStep10BstordPrc": 102000,
                "bidStep1BstordRqty": 71429,
                "bidStep2BstordRqty": 136398,
                "bidStep3BstordRqty": 103213,
                "bidStep4BstordRqty": 80745,
                "bidStep5BstordRqty": 34063,
                "bidStep6BstordRqty": 26098,
                "bidStep7BstordRqty": 13065,
                "bidStep8BstordRqty": 50927,
                "bidStep9BstordRqty": 11651,
                "bidStep10BstordRqty": 25900,
                "askordTotRqty": 442078,
                "bidordTotRqty": 553489,
                "pstoffhrAskTotOrdRqty": 3946,
                "pstoffhrBidTotOrdRqty": 0,
                "accTrdvol": 3066512,
                "deemTrdPrc": 107000,
                "deemTrdvol": 1,
                "deemAccTrdvol": 152589,
                "isuSrtCd": "000660"
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/kospi/multiquote/stocks/orderbook?isuCd=005930,000660'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isulist": [
            {
                "askStep1BstordPrc": 66700,
                "askStep2BstordPrc": 66800,
                "askStep3BstordPrc": 66900,
                "askStep4BstordPrc": 67000,
                "askStep5BstordPrc": 67100,
                "askStep6BstordPrc": 67200,
                "askStep7BstordPrc": 67300,
                "askStep8BstordPrc": 67400,
                "askStep9BstordPrc": 67500,
                "askStep10BstordPrc": 67600,
                "askStep1BstordRqty": 10663,
                "askStep2BstordRqty": 241244,
                "askStep3BstordRqty": 152601,
                "askStep4BstordRqty": 116059,
                "askStep5BstordRqty": 32390,
                "askStep6BstordRqty": 22328,
                "askStep7BstordRqty": 20267,
                "askStep8BstordRqty": 41831,
                "askStep9BstordRqty": 46067,
                "askStep10BstordRqty": 25594,
                "bidStep1BstordPrc": 66600,
                "bidStep2BstordPrc": 66500,
                "bidStep3BstordPrc": 66400,
                "bidStep4BstordPrc": 66300,
                "bidStep5BstordPrc": 66200,
                "bidStep6BstordPrc": 66100,
                "bidStep7BstordPrc": 66000,
                "bidStep8BstordPrc": 65900,
                "bidStep9BstordPrc": 65800,
                "bidStep10BstordPrc": 65700,
                "bidStep1BstordRqty": 73314,
                "bidStep2BstordRqty": 72871,
                "bidStep3BstordRqty": 419704,
                "bidStep4BstordRqty": 282534,
                "bidStep5BstordRqty": 209295,
                "bidStep6BstordRqty": 198780,
                "bidStep7BstordRqty": 405176,
                "bidStep8BstordRqty": 65606,
                "bidStep9BstordRqty": 73575,
                "bidStep10BstordRqty": 46276,
                "askordTotRqty": 709044,
                "bidordTotRqty": 1847131,
                "pstoffhrAskTotOrdRqty": 0,
                "pstoffhrBidTotOrdRqty": 3661,
                "accTrdvol": 13842806,
                "deemTrdPrc": 66700,
                "deemTrdvol": 1,
                "deemAccTrdvol": 1194589,
                "isuSrtCd": "005930"
            },
            {
                "askStep1BstordPrc": 107000,
                "askStep2BstordPrc": 107500,
                "askStep3BstordPrc": 108000,
                "askStep4BstordPrc": 108500,
                "askStep5BstordPrc": 109000,
                "askStep6BstordPrc": 109500,
                "askStep7BstordPrc": 110000,
                "askStep8BstordPrc": 110500,
                "askStep9BstordPrc": 111000,
                "askStep10BstordPrc": 111500,
                "askStep1BstordRqty": 2615,
                "askStep2BstordRqty": 82113,
                "askStep3BstordRqty": 66430,
                "askStep4BstordRqty": 56091,
                "askStep5BstordRqty": 47491,
                "askStep6BstordRqty": 39123,
                "askStep7BstordRqty": 66341,
                "askStep8BstordRqty": 24777,
                "askStep9BstordRqty": 27659,
                "askStep10BstordRqty": 29438,
                "bidStep1BstordPrc": 106500,
                "bidStep2BstordPrc": 106000,
                "bidStep3BstordPrc": 105500,
                "bidStep4BstordPrc": 105000,
                "bidStep5BstordPrc": 104500,
                "bidStep6BstordPrc": 104000,
                "bidStep7BstordPrc": 103500,
                "bidStep8BstordPrc": 103000,
                "bidStep9BstordPrc": 102500,
                "bidStep10BstordPrc": 102000,
                "bidStep1BstordRqty": 71429,
                "bidStep2BstordRqty": 136398,
                "bidStep3BstordRqty": 103213,
                "bidStep4BstordRqty": 80745,
                "bidStep5BstordRqty": 34063,
                "bidStep6BstordRqty": 26098,
                "bidStep7BstordRqty": 13065,
                "bidStep8BstordRqty": 50927,
                "bidStep9BstordRqty": 11651,
                "bidStep10BstordRqty": 25900,
                "askordTotRqty": 442078,
                "bidordTotRqty": 553489,
                "pstoffhrAskTotOrdRqty": 3946,
                "pstoffhrBidTotOrdRqty": 0,
                "accTrdvol": 3066512,
                "deemTrdPrc": 107000,
                "deemTrdvol": 1,
                "deemAccTrdvol": 152589,
                "isuSrtCd": "000660"
            }
        ]
    }
}
```



## KOSPI 주식종목 체결 API  <a href="#api" id="api"></a>

* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi/stocks" path="/{issuecode}/price" method="get" summary="/v3/market/realtime/kospi/stocks/{issuecode}/price" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)005930
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "005930",
        "trdPrc": 66700,
        "cmpprevddTpCd": "5",
        "opnprc": 66600,
        "hgprc": 67000,
        "lwprc": 66400,
        "accTrdvol": 13844624,
        "trdTm": 15554100,
        "trdvol": 10,
        "accTrdval": 922352871000,
        "cmpprevddPrc": -700,
        "bidordPrc_1": 66600,
        "askordPrc_1": 66700,
        "lstAskbidTpCd": 1
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/stocks/005930/price'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "005930",
        "trdPrc": 66700,
        "cmpprevddTpCd": "5",
        "opnprc": 66600,
        "hgprc": 67000,
        "lwprc": 66400,
        "accTrdvol": 13844624,
        "trdTm": 15554100,
        "trdvol": 10,
        "accTrdval": 922352871000,
        "cmpprevddPrc": -700,
        "bidordPrc_1": 66600,
        "askordPrc_1": 66700,
        "lstAskbidTpCd": 1
    }
}
```



## KOSPI 주식 종목 호가잔량 (LP호가제외) API  <a href="#api" id="api"></a>

* 종목 호가잔량 (LP호가 제외)
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi/stocks" path="/{issuecode}/orderbook" method="get" summary="/v3/market/realtime/kospi/stocks/{issuecode}/orderbook" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)005930
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "005930",
        "askStep1BstordPrc": 66700,
        "askStep2BstordPrc": 66800,
        "askStep3BstordPrc": 66900,
        "askStep4BstordPrc": 67000,
        "askStep5BstordPrc": 67100,
        "askStep6BstordPrc": 67200,
        "askStep7BstordPrc": 67300,
        "askStep8BstordPrc": 67400,
        "askStep9BstordPrc": 67500,
        "askStep10BstordPrc": 67600,
        "askStep1BstordRqty": 10663,
        "askStep2BstordRqty": 241244,
        "askStep3BstordRqty": 152601,
        "askStep4BstordRqty": 116059,
        "askStep5BstordRqty": 32390,
        "askStep6BstordRqty": 22328,
        "askStep7BstordRqty": 20267,
        "askStep8BstordRqty": 41831,
        "askStep9BstordRqty": 46067,
        "askStep10BstordRqty": 25594,
        "bidStep1BstordPrc": 66600,
        "bidStep2BstordPrc": 66500,
        "bidStep3BstordPrc": 66400,
        "bidStep4BstordPrc": 66300,
        "bidStep5BstordPrc": 66200,
        "bidStep6BstordPrc": 66100,
        "bidStep7BstordPrc": 66000,
        "bidStep8BstordPrc": 65900,
        "bidStep9BstordPrc": 65800,
        "bidStep10BstordPrc": 65700,
        "bidStep1BstordRqty": 73314,
        "bidStep2BstordRqty": 72871,
        "bidStep3BstordRqty": 419704,
        "bidStep4BstordRqty": 282534,
        "bidStep5BstordRqty": 209295,
        "bidStep6BstordRqty": 198780,
        "bidStep7BstordRqty": 405176,
        "bidStep8BstordRqty": 65606,
        "bidStep9BstordRqty": 73575,
        "bidStep10BstordRqty": 46276,
        "askordTotRqty": 709044,
        "bidordTotRqty": 1847131,
        "pstoffhrAskTotOrdRqty": 0,
        "pstoffhrBidTotOrdRqty": 2895,
        "accTrdvol": 13844794,
        "deemTrdPrc": 66700,
        "deemTrdvol": 1,
        "deemAccTrdvol": 1194589
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/stocks/005930/orderbook'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "005930",
        "askStep1BstordPrc": 66700,
        "askStep2BstordPrc": 66800,
        "askStep3BstordPrc": 66900,
        "askStep4BstordPrc": 67000,
        "askStep5BstordPrc": 67100,
        "askStep6BstordPrc": 67200,
        "askStep7BstordPrc": 67300,
        "askStep8BstordPrc": 67400,
        "askStep9BstordPrc": 67500,
        "askStep10BstordPrc": 67600,
        "askStep1BstordRqty": 10663,
        "askStep2BstordRqty": 241244,
        "askStep3BstordRqty": 152601,
        "askStep4BstordRqty": 116059,
        "askStep5BstordRqty": 32390,
        "askStep6BstordRqty": 22328,
        "askStep7BstordRqty": 20267,
        "askStep8BstordRqty": 41831,
        "askStep9BstordRqty": 46067,
        "askStep10BstordRqty": 25594,
        "bidStep1BstordPrc": 66600,
        "bidStep2BstordPrc": 66500,
        "bidStep3BstordPrc": 66400,
        "bidStep4BstordPrc": 66300,
        "bidStep5BstordPrc": 66200,
        "bidStep6BstordPrc": 66100,
        "bidStep7BstordPrc": 66000,
        "bidStep8BstordPrc": 65900,
        "bidStep9BstordPrc": 65800,
        "bidStep10BstordPrc": 65700,
        "bidStep1BstordRqty": 73314,
        "bidStep2BstordRqty": 72871,
        "bidStep3BstordRqty": 419704,
        "bidStep4BstordRqty": 282534,
        "bidStep5BstordRqty": 209295,
        "bidStep6BstordRqty": 198780,
        "bidStep7BstordRqty": 405176,
        "bidStep8BstordRqty": 65606,
        "bidStep9BstordRqty": 73575,
        "bidStep10BstordRqty": 46276,
        "askordTotRqty": 709044,
        "bidordTotRqty": 1847131,
        "pstoffhrAskTotOrdRqty": 0,
        "pstoffhrBidTotOrdRqty": 2895,
        "accTrdvol": 13844794,
        "deemTrdPrc": 66700,
        "deemTrdvol": 1,
        "deemAccTrdvol": 1194589
    }
}
```

## KOSPI 주식 종목 일중 API  <a href="#api" id="api"></a>

* 종목 일중 데이터 제공 \[10초, 1분, 10분단위 시/고/저/종]
* 최대 100건 까지만 조회 가능
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi/stocks" path="/{issuecode}/intraday" method="get" summary="/v3/market/realtime/kospi/stocks/{issuecode}/intraday" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)005930
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
        "isuSrtCd": "005930",
        "hisLists": [
            {
                "inddTm": "10000000",
                "inddOpnprc": 66500,
                "inddHgprc": 66800,
                "inddLwprc": 66400,
                "inddClsprc": 66800,
                "inddTrdvol": 1577394,
                "inddTrdval": 105061416800,
                "inddAccTrdvol": 11340696,
                "inddAccTrdval": 750382201300
            },
            {
                "inddTm": "9100000",
                "inddOpnprc": 65100,
                "inddHgprc": 66000,
                "inddLwprc": 65000,
                "inddClsprc": 66000,
                "inddTrdvol": 3472896,
                "inddTrdval": 227416478800,
                "inddAccTrdvol": 3472896,
                "inddAccTrdval": 227416478800
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/stocks/005930/intraday?inddCycleTpCd=600&inqStrtDd=20220501&strtTm=0900&endTm=1500'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "005930",
        "hisLists": [
            {
                "inddTm": "10000000",
                "inddOpnprc": 66500,
                "inddHgprc": 66800,
                "inddLwprc": 66400,
                "inddClsprc": 66800,
                "inddTrdvol": 1577394,
                "inddTrdval": 105061416800,
                "inddAccTrdvol": 11340696,
                "inddAccTrdval": 750382201300
            },
            {
                "inddTm": "9100000",
                "inddOpnprc": 65100,
                "inddHgprc": 66000,
                "inddLwprc": 65000,
                "inddClsprc": 66000,
                "inddTrdvol": 3472896,
                "inddTrdval": 227416478800,
                "inddAccTrdvol": 3472896,
                "inddAccTrdval": 227416478800
            }
        ]
    }
}
```



## KOSPI 주식 거래상위 회원사 정보 API  <a href="#api" id="api"></a>

* 종목 매수/매도 상위 5개 회원사 정보
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/kospi/stocks" path="/{issuecode}/traderanking" method="get" summary="/v3/market/realtime/kospi/stocks/{issuecode}/traderanking" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="issuecode" type="string" required="true" %}
종목코드 ex)005930
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "005930*001",
        "askTrdVolMbr1": 1602594,
        "askTrdVolMbr2": 1546376,
        "askTrdVolMbr3": 1523917,
        "askTrdVolMbr4": 1409545,
        "askTrdVolMbr5": 1022395,
        "askTrdAmtMbr1": 106720756800,
        "askTrdAmtMbr2": 103036585600,
        "askTrdAmtMbr3": 101470996800,
        "askTrdAmtMbr4": 93890130800,
        "askTrdAmtMbr5": 68138125500,
        "askTrdWtMbr1": 11.58,
        "askTrdWtMbr2": 11.18,
        "askTrdWtMbr3": 11.01,
        "askTrdWtMbr4": 10.19,
        "askTrdWtMbr5": 7.39,
        "bidTrdVolMbr1": 2123403,
        "bidTrdVolMbr2": 1542124,
        "bidTrdVolMbr3": 1187107,
        "bidTrdVolMbr4": 1051463,
        "bidTrdVolMbr5": 979252,
        "bidTrdAmtMbr1": 141505144700,
        "bidTrdAmtMbr2": 102754795900,
        "bidTrdAmtMbr3": 79074334000,
        "bidTrdAmtMbr4": 70038390000,
        "bidTrdAmtMbr5": 65233490700,
        "bidTrdWtMbr1": 15.35,
        "bidTrdWtMbr2": 11.15,
        "bidTrdWtMbr3": 8.58,
        "bidTrdWtMbr4": 7.6,
        "bidTrdWtMbr5": 7.08,
        "bidTrdPrcMbr1": 66641,
        "bidTrdPrcMbr2": 66632,
        "bidTrdPrcMbr3": 66611,
        "bidTrdPrcMbr4": 66610,
        "bidTrdPrcMbr5": 66616,
        "askTrdPrcMbr1": 66593,
        "askTrdPrcMbr2": 66631,
        "askTrdPrcMbr3": 66586,
        "askTrdPrcMbr4": 66610,
        "askTrdPrcMbr5": 66646,
        "bidTrdMbr1": "씨티그룹",
        "bidTrdMbr2": "이베스트투자증권",
        "bidTrdMbr3": "삼성증권",
        "bidTrdMbr4": "키움증권",
        "bidTrdMbr5": "미래에셋증권",
        "askTrdMbr1": "제이피모간",
        "askTrdMbr2": "이베스트투자증권",
        "askTrdMbr3": "모간스탠리",
        "askTrdMbr4": "삼성증권",
        "askTrdMbr5": "한화투자"
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
'https://testoap.k-mydata.org/v3/market/realtime/kospi/stocks/005930/traderanking'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "005930*001",
        "askTrdVolMbr1": 1602594,
        "askTrdVolMbr2": 1546376,
        "askTrdVolMbr3": 1523917,
        "askTrdVolMbr4": 1409545,
        "askTrdVolMbr5": 1022395,
        "askTrdAmtMbr1": 106720756800,
        "askTrdAmtMbr2": 103036585600,
        "askTrdAmtMbr3": 101470996800,
        "askTrdAmtMbr4": 93890130800,
        "askTrdAmtMbr5": 68138125500,
        "askTrdWtMbr1": 11.58,
        "askTrdWtMbr2": 11.18,
        "askTrdWtMbr3": 11.01,
        "askTrdWtMbr4": 10.19,
        "askTrdWtMbr5": 7.39,
        "bidTrdVolMbr1": 2123403,
        "bidTrdVolMbr2": 1542124,
        "bidTrdVolMbr3": 1187107,
        "bidTrdVolMbr4": 1051463,
        "bidTrdVolMbr5": 979252,
        "bidTrdAmtMbr1": 141505144700,
        "bidTrdAmtMbr2": 102754795900,
        "bidTrdAmtMbr3": 79074334000,
        "bidTrdAmtMbr4": 70038390000,
        "bidTrdAmtMbr5": 65233490700,
        "bidTrdWtMbr1": 15.35,
        "bidTrdWtMbr2": 11.15,
        "bidTrdWtMbr3": 8.58,
        "bidTrdWtMbr4": 7.6,
        "bidTrdWtMbr5": 7.08,
        "bidTrdPrcMbr1": 66641,
        "bidTrdPrcMbr2": 66632,
        "bidTrdPrcMbr3": 66611,
        "bidTrdPrcMbr4": 66610,
        "bidTrdPrcMbr5": 66616,
        "askTrdPrcMbr1": 66593,
        "askTrdPrcMbr2": 66631,
        "askTrdPrcMbr3": 66586,
        "askTrdPrcMbr4": 66610,
        "askTrdPrcMbr5": 66646,
        "bidTrdMbr1": "씨티그룹",
        "bidTrdMbr2": "이베스트투자증권",
        "bidTrdMbr3": "삼성증권",
        "bidTrdMbr4": "키움증권",
        "bidTrdMbr5": "미래에셋증권",
        "askTrdMbr1": "제이피모간",
        "askTrdMbr2": "이베스트투자증권",
        "askTrdMbr3": "모간스탠리",
        "askTrdMbr4": "삼성증권",
        "askTrdMbr5": "한화투자"
    }
}
```



