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



## 업종 일중 API  <a href="#api" id="api"></a>

* 전체 업종 일중 데이터 제공 \[10초, 1분, 10분단위 시/고/저/종]
* 제공시간 : 실시간
* 최대 100건 까지만 조회 가능

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/index" path="/{marketcode}/{issuecode}/intraday" method="get" summary="/v3/market/realtime/index/{marketcode}/{issuecode}/intraday" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" required="true" name="marketcode" %}
ex) kospi
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="issuecode" %}
ex) K1
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inddCycleTpCd" required="true" %}
일중 전송주기 구분코드 [10:10초, 60:1분, 600:10분]
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" %}
조회시작일자 YYYYMMSS
{% endswagger-parameter %}

{% swagger-parameter in="query" name="strtTm" required="true" %}
개시시각,시작시각 HHMM
{% endswagger-parameter %}

{% swagger-parameter in="query" name="endTm" required="true" %}
종료시각 HHMM
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "hisLists": [
            {
                "inddTm": "13000000",
                "inddOpnprc": 2670.72,
                "inddHgprc": 2671.42,
                "inddLwprc": 2669.18,
                "inddClsprc": 2670.08,
                "inddTrdvol": 5566,
                "inddTrdval": 102637,
                "inddAccTrdvol": 332849,
                "inddAccTrdval": 4929515
            },
            {
                "inddTm": "12500000",
                "inddOpnprc": 2667.84,
                "inddHgprc": 2670.6,
                "inddLwprc": 2667.84,
                "inddClsprc": 2670.07,
                "inddTrdvol": 4948,
                "inddTrdval": 112555,
                "inddAccTrdvol": 327283,
                "inddAccTrdval": 4826878
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**      | **Type**   | **Description** |                             |
| ------------- | ---------- | --------------- | --------------------------- |
| isuSrtCd      | String(3)  | 업종코드            |                             |
| isuNm         | String(80) | 종목명             |                             |
| hisLists      | Array(4)   | 과거리스트           |                             |
| inddTm        | string(8)  | 일중시간            | HH:MM:SS                    |
| inddOpnprc    | number(11) | 일중시가            | 일중데이타(10초, 1분, 10분)         |
| inddHgprc     | number(11) | 일중고가            | 일중데이타(10초, 1분, 10분)         |
| inddLwprc     | number(11) | 일중저가            | 일중데이타(10초, 1분, 10분)         |
| inddClsprc    | number(11) | 일중종가            | 일중데이타(10초, 1분, 10분)         |
| inddTrdvol    | number(11) | 일중거래량           | 일중데이타(10초, 1분, 10분)         |
| inddTrdval    | number(11) | 일중거래대금          | 일중데이타(10초, 1분, 10분) 구간 거래대금 |
| inddAccTrdvol | number(11) | 일중누적거래량         |                             |
| inddAccTrdval | number(11) | 일중누적대금          |                             |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/index/kospi/K1/intraday?inddCycleTpCd=600&inqStrtDd=20220530&strtTm=0900&endTm=1300'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "hisLists": [
            {
                "inddTm": "13000000",
                "inddOpnprc": 2670.72,
                "inddHgprc": 2671.42,
                "inddLwprc": 2669.18,
                "inddClsprc": 2670.08,
                "inddTrdvol": 5566,
                "inddTrdval": 102637,
                "inddAccTrdvol": 332849,
                "inddAccTrdval": 4929515
            },
            {
                "inddTm": "12500000",
                "inddOpnprc": 2667.84,
                "inddHgprc": 2670.6,
                "inddLwprc": 2667.84,
                "inddClsprc": 2670.07,
                "inddTrdvol": 4948,
                "inddTrdval": 112555,
                "inddAccTrdvol": 327283,
                "inddAccTrdval": 4826878
            }
        ]
    }
}
```



## 업종 지수 API  <a href="#api" id="api"></a>

* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/index" path="/{marketcode}/{issuecode}/index" method="get" summary="/v3/market/realtime/index/{marketcode}/{issuecode}/index" %}
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
        "trdPrc": 2669.78,
        "cmpprevddTpCd": "2",
        "accTrdvol": 472530,
        "trdTm": 14191000,
        "accTrdval": 6055505,
        "cmpprevddPrc": 10.79
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**      | **Type**   | **Description** |                                                      |
| ------------- | ---------- | --------------- | ---------------------------------------------------- |
| isuSrtCd      | String(3)  | 업종코드            | 업종코드표 참조                                             |
| trdTm         | String(8)  | 체결시각,거래시각       | \*테이블 하단 참고                                          |
| trdPrc        | number(10) | 지수              |                                                      |
| cmpprevddTpCd | String(1)  | 전일대비구분코드        | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc  | number(11) | 전일대비지수          |                                                      |
| accTrdvol     | number(12) | 누적체결수량,누적거래량    | 단위:주                                                 |
| accTrdval     | number(22) | 누적거래대금          | 단위:원                                                 |

> `trdTm`\
> "HHMMSSmm" 형태로 시간전송
>
> * 정규장 개시전 또는 정규장 체결 발생 이전 : 0 &#x20;
> *   장운영시그널, 대량체결 포함 &#x20;
>
>     _※ 장운영시그널_ &#x20;
>
>     정규장마감(15:00):31000000 /장종료시간외마감(15:30):41000000 /단일가마감(18:00):81000000 /일반Buy-in마감(18:00):91000007 /당일Buy-in마감(18:00):91000008 &#x20;
>
>     _※ 대량체결시_  &#x20;
>
>     장전대량매매체결:51000000/장중대량매매체결:61000000/장후대량매매체결:71000000"

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/index/kospi/K1/index'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K1",
        "trdPrc": 2669.78,
        "cmpprevddTpCd": "2",
        "accTrdvol": 472530,
        "trdTm": 14191000,
        "accTrdval": 6055505,
        "cmpprevddPrc": 10.79
    }
}
```



## 업종 투자자별 매매동향 API  <a href="#api" id="api"></a>

* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/index" path="/{marketcode}/{issuecode}/investors" method="get" summary="/v3/market/realtime/index/{marketcode}/{issuecode}/investors" %}
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
        "Tm": "14240000",
        "isuSrtCd": "K1",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 4403020,
                "askTrdval": 207768090,
                "bidTrdvol": 5407468,
                "bidTrdval": 263499590
            },
            {
                "invstCd": "02",
                "askTrdvol": 1076736,
                "askTrdval": 44161903,
                "bidTrdvol": 875646,
                "bidTrdval": 41366089
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

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
'https://testoap.k-mydata.org/v3/market/realtime/index/kospi/K1/investors'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "14240000",
        "isuSrtCd": "K1",
        "invstLists": [
            {
                "invstCd": "01",
                "askTrdvol": 4403020,
                "askTrdval": 207768090,
                "bidTrdvol": 5407468,
                "bidTrdval": 263499590
            },
            {
                "invstCd": "02",
                "askTrdvol": 1076736,
                "askTrdval": 44161903,
                "bidTrdvol": 875646,
                "bidTrdval": 41366089
            }
        ]
    }
}
```

