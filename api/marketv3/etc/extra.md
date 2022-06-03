# 부가서비스

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## ETF 구성종목 정보 API  <a href="#api" id="api"></a>

* ETF 종목코드를 이용한 구성종목정보 제공
* 종목명 기준으로 ETF구성종목 정보를 편리하게 수신할수 있는 ETF PDF 파일 가공 서비스
* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/extra/stocks" path="/{marketcode}/{issuecode}/pdf" method="get" summary="/v3/market/extra/stocks/{marketcode}/{issuecode}/pdf" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi | kosdaq
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 069500
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "Cnt": "200",
    "InqDd": "20220603",
    "Lists": [
        {
            "isuCd": "KR7000070003",
            "Unit": 6,
            "isuNm": "삼양홀딩스",
            "SetAmt": 483600,
            "ratio": 0.02
        },
        {
            "isuCd": "KR7000080002",
            "Unit": 49,
            "isuNm": "하이트진로",
            "SetAmt": 1781150,
            "ratio": 0.10
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/extra/stocks/kospi/069500/pdf'
```

#### Response Example

```yaml
{
    "Cnt": "200",
    "InqDd": "20220603",
    "Lists": [
        {
            "isuCd": "KR7000070003",
            "Unit": 6,
            "isuNm": "삼양홀딩스",
            "SetAmt": 483600,
            "ratio": 0.02
        },
        {
            "isuCd": "KR7000080002",
            "Unit": 49,
            "isuNm": "하이트진로",
            "SetAmt": 1781150,
            "ratio": 0.10
        }
    ]
}
```



## ETF 종목 nav 조회 API  <a href="#api" id="api"></a>

* ETF 종목코드를 이용한 nav(순자산가치) 현재가 조회
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/extra/stocks" path="/{marketcode}/{issuecode}/nav" method="get" summary="/v3/market/extra/stocks/{marketcode}/{issuecode}/nav" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi | kosdaq
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 069500
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "069500",
        "nav": 35255.08,
        "cmpprevddNav": 138.33
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response **Parameters**

| **Name**     | **Type**   | **Description** |                             |
| ------------ | ---------- | --------------- | --------------------------- |
| isuSrtCd     | string(9)  | 종목단축코드          |                             |
| nav          | number(11) | 순자산가치           | 당일 NAV (ETF종목만 존재, 소수점 2자리) |
| cmpprevddNav | number(11) | 전일대비 순자산가치      |                             |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/extra/stocks/kospi/069500/nav'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "069500",
        "nav": 35255.08,
        "cmpprevddNav": 138.33
    }
}
```



## ETF 종목 nav 히스토리 API  <a href="#api" id="api"></a>

* ETF 종목 일별 과거 nav(순자산가치) 데이터 제공
* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/extra/stocks" path="/{marketcode}/{issuecode}/navhistory" method="get" summary="/v3/market/extra/stocks/{marketcode}/{issuecode}/navhistory" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi | kosdaq
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 069500
{% endswagger-parameter %}

{% swagger-parameter in="query" name="trnsmCycleTpCd" required="true" %}
전송주기구분코드 [D:일, W:주, M:월] 해당기간의 마지막영업일 기준 시세임. 예) W:주-금요일, M:월-31일
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" required="true" %}
조회시작일자 YYYYMMDD
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqEndDd" required="true" %}
조회종료일자 YYYYMMDD
{% endswagger-parameter %}

{% swagger-parameter in="query" name="reqCnt" %}
요청건수 (최대 100건)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "069500",
        "hisLists": [
            {
                "trdDd": 20220503,
                "trdPrc": 35290,
                "nav": 35398.24,
                "cmpprevddNav": -70.74
            },
            {
                "trdDd": 20220502,
                "trdPrc": 35375,
                "nav": 35468.98,
                "cmpprevddNav": -105.6
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response **Parameters**

| **Name**     | **Type**   | **Description** |                             |
| ------------ | ---------- | --------------- | --------------------------- |
| isuSrtCd     | string(9)  | 종목단축코드          |                             |
| hisLists     | Array(4)   | 과거리스트           |                             |
| trdDd        | string(8)  | 체결일자,거래일자,매매일자  | YYYYMMDD                    |
| nav          | number(11) | 순자산가치           | 당일 NAV (ETF종목만 존재, 소수점 2자리) |
| cmpprevddNav | number(11) | 전일대비 순자산가치      |                             |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/extra/stocks/kospi/069500/navhistory?trnsmCycleTpCd=D&inqStrtDd=20220501&inqEndDd=20220503&reqCnt=2'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "069500",
        "hisLists": [
            {
                "trdDd": 20220503,
                "trdPrc": 35290,
                "nav": 35398.24,
                "cmpprevddNav": -70.74
            },
            {
                "trdDd": 20220502,
                "trdPrc": 35375,
                "nav": 35468.98,
                "cmpprevddNav": -105.6
            }
        ]
    }
}
```





## 국가별 휴장일 정보 API  <a href="#api" id="api"></a>

* 국가별 현재일 이후의 휴장일 정보 (부정기 갱신으로 항시 데이터 변경 가능성 존재)
* 제공시간 : 실시간(부정기갱신)

{% swagger baseUrl="https://{APIGWAddr}/v3/market/extra/stocks" path="/{nationcode}/holiday" method="get" summary="/v3/market/extra/stocks/{nationcode}/holiday" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="nationcode" required="true" %}
ex) KR
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "marketCd": "KR",
    "lists": [
        "20220606",
        "20220815",
        "20220909",
        "20220912",
        "20221003",
        "20221010",
        "20221230"
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/extra/stocks/KR/holiday'
```

#### Response Example

```yaml
{
    "marketCd": "KR",
    "lists": [
        "20220606",
        "20220815",
        "20220909",
        "20220912",
        "20221003",
        "20221010",
        "20221230"
    ]
}
```









