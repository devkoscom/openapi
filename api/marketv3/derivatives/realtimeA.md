# 파생실시간A

상품/지수 선물시장과 옵션시장에 상장된 종목 리스트, 종목 마스터 등 종가 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## 상품/지수 선물 체결 API  <a href="#api" id="api"></a>

* 데이터 발생시마다 실시간 제공
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/futures/{marketcode}/{issuecode}/price" method="get" summary="/v3/market/realtime/derivative/futures/{marketcode}/{issuecode}/price" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) K2FA001
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "101S6000",
        "trdPrc": 352,
        "opnprc": 353.25,
        "hgprc": 353.85,
        "lwprc": 351.15,
        "accTrdvol": 116262,
        "trdTm": 10492759,
        "trdvol": 2,
        "lstTrdTpCd": 2,
        "accTrdval": 10245976050000,
        "fstmmAgndaContrtPrc": 352,
        "futrmmAgndaContrtPrc": 0,
        "negoBlkAccTrdvol": 0,
        "realtmUplmtprc": 355.5,
        "realtmLwlmtprc": 348.5
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**             | **Type**   | **Description** |                                       |
| -------------------- | ---------- | --------------- | ------------------------------------- |
| isuSrtCd             | string(12) | 종목단축코드          | 표준코드&#xD;                             |
| trdPrc               | number(11) | 체결가격            |                                       |
| trdvol               | number(10) | 체결수량, 거래량       | 단위:주                                  |
| trdTm                | string(8)  | 체결시각,거래시각       |                                       |
| fstmmAgndaContrtPrc  | number(11) | 최근월물의제약정가격      |                                       |
| futrmmAgndaContrtPrc | number(11) | 원월물의제약정가격       |                                       |
| opnprc               | number(11) | 시가              | 단위:원                                  |
| hgprc                | number(11) | 고가              | 단위:원                                  |
| lwprc                | number(11) | 저가              | 단위:원                                  |
| accTrdvol            | number(12) | 누적체결수량,누적거래량    | 일반체결수량+협의대량체결수량+EFP누적체결수량 /2009.08.31 |
| accTrdval            | number(22) | 누적거래대금          | 일반체결대금+협의대량체결대금+EFP누적체결대금 /2009.08.31 |
| negoBlkAccTrdvol     | number(12) | 협의대량누적체결수량      |                                       |
| lstAskbidTpCd        | string(1)  | 최종매도매수구분코드      | 1:매도, 2:매수 (최종으로 들어온 호가의 매도매수구분값)     |
| realtmUplmtprc       | number(11) | 실시간상한가          |                                       |
| realtmLwlmtprc       | number(11) | 실시간하한가          |                                       |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/derivative/futures/kospi200/K2FA001/master'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "101S6000",
        "midyyHgstprc": 399.35,
        "midyyHgstprcDd": 20220103,
        "midyyLwstprc": 337.1,
        "midyyLwstprcDd": 20220512,
        "inlistHgstprc": 428.9,
        "inlistHgstprcDd": 20210614,
        "inlistLwstprc": 306.55,
        "inlistLwstprcDd": 20200826,
        "prevddClsprc": 350,
        "prevddOpnprc": 351.85,
        "prevddHgprc": 352.35,
        "prevddLwprc": 349.3,
        "prevddAccTrdvol": 226772,
        "prevddAccTrdval": 19868464712500,
        "prevddOpnintQty": 290464,
        "setlPrcTheoPrcDivrgRt": -0.06,
        "trdDd": 20220603,
        "basPrc": 350,
        "isuKorNm": "KOSPI200 선물 2206",
        "isuKorAbbrv": "K200 선물 2206",
        "isuCd": "KR4101S60008",
        "listDd": 20200612,
        "remainDys": 7,
        "cdInt": 1.96,
        "lsttrdDd": 20220609,
        "expDd": 202206,
        "ulyId": "KOSPI200",
        "prcLmtStep1Uplmtprc": 378,
        "prcLmtStep2Uplmtprc": 402.5,
        "prcLmtStep3Uplmtprc": 420,
        "prcLmtStep1Lwlmtprc": 322,
        "prcLmtStep2Lwlmtprc": 297.5,
        "prcLmtStep3Lwlmtprc": 280,
        "opnintLmtQty": null,
        "setlmult": 250000,
        "setlTheoPrc": null,
        "basTheoPrc": null
    }
}
```



## 상품/지수 선물 우선호가 API  <a href="#api" id="api"></a>

* 데이터 발생시마다 실시간 제공
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/futures/{marketcode}/{issuecode}/orderbook" method="get" summary="/v3/market/realtime/derivative/futures/{marketcode}/{issuecode}/orderbook" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) K2FA001
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "101S6000",
        "askStep1BstordPrc": 352.05,
        "askStep2BstordPrc": 352.1,
        "askStep3BstordPrc": 352.15,
        "askStep4BstordPrc": 352.2,
        "askStep5BstordPrc": 352.25,
        "askStep1BstordRqty": 48,
        "askStep2BstordRqty": 132,
        "askStep3BstordRqty": 183,
        "askStep4BstordRqty": 255,
        "askStep5BstordRqty": 140,
        "bidStep1BstordPrc": 352,
        "bidStep2BstordPrc": 351.95,
        "bidStep3BstordPrc": 351.9,
        "bidStep4BstordPrc": 351.85,
        "bidStep5BstordPrc": 351.8,
        "bidStep1BstordRqty": 93,
        "bidStep2BstordRqty": 214,
        "bidStep3BstordRqty": 168,
        "bidStep4BstordRqty": 143,
        "bidStep5BstordRqty": 166,
        "askTotOrdRqty": 16817,
        "bidTotOrdRqty": 15742,
        "askStep1BstordCnt": 27,
        "bidStep1BstordCnt": 33,
        "askStep2BstordCnt": 56,
        "bidStep2BstordCnt": 52,
        "askStep3BstordCnt": 75,
        "bidStep3BstordCnt": 62,
        "askStep4BstordCnt": 70,
        "bidStep4BstordCnt": 60,
        "askStep5BstordCnt": 53,
        "bidStep5BstordCnt": 55,
        "askValidOrdCnt": 3037,
        "bidValidOrdCnt": 2568,
        "ordAcptTm": 10524400,
        "deemTrdPrc": 353.25
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**           | **Type**   | **Description** |          |
| ------------------ | ---------- | --------------- | -------- |
| isuSrtCd           | String(12) | 종목단축코드          | 단축코드     |
| bidTotOrdRqty      | number(12) | 매수총호가잔량         |          |
| bidStep1BstordPrc  | number(11) | 매수1단계우선호가가격     |          |
| bidStep1BstordRqty | number(12) | 매수1단계우선호가잔량     |          |
| bidStep2BstordPrc  | number(11) | 매수2단계우선호가가격     |          |
| bidStep2BstordRqty | number(12) | 매수2단계우선호가잔량     |          |
| bidStep3BstordPrc  | number(11) | 매수3단계우선호가가격     |          |
| bidStep3BstordRqty | number(12) | 매수3단계우선호가잔량     |          |
| bidStep4BstordPrc  | number(11) | 매수4단계우선호가가격     |          |
| bidStep4BstordRqty | number(12) | 매수4단계우선호가잔량     |          |
| bidStep5BstordPrc  | number(11) | 매수5단계우선호가가격     |          |
| bidStep5BstordRqty | number(12) | 매수5단계우선호가잔량     |          |
| askTotOrdRqty      | number(12) | 매도총호가잔량         |          |
| askStep1BstordPrc  | number(11) | 매도1단계우선호가가격     |          |
| askStep1BstordRqty | number(12) | 매도1단계우선호가잔량     |          |
| askStep2BstordPrc  | number(11) | 매도2단계우선호가가격     |          |
| askStep2BstordRqty | number(12) | 매도2단계우선호가잔량     |          |
| askStep3BstordPrc  | number(11) | 매도3단계우선호가가격     |          |
| askStep3BstordRqty | number(12) | 매도3단계우선호가잔량     |          |
| askStep4BstordPrc  | number(11) | 매도4단계우선호가가격     |          |
| askStep4BstordRqty | number(12) | 매도4단계우선호가잔량     |          |
| askStep5BstordPrc  | number(11) | 매도5단계우선호가가격     |          |
| askStep5BstordRqty | number(12) | 매도5단계우선호가잔량     |          |
| bidValidOrdCnt     | number(11) | 매수유효호가건수        |          |
| bidStep1BstordCnt  | number(11) | 매수1단계우선호가건수     |          |
| bidStep2BstordCnt  | number(11) | 매수2단계우선호가건수     |          |
| bidStep3BstordCnt  | number(11) | 매수3단계우선호가건수     |          |
| bidStep4BstordCnt  | number(11) | 매수4단계우선호가건수     |          |
| bidStep5BstordCnt  | number(11) | 매수5단계우선호가건수     |          |
| askValidOrdCnt     | number(11) | 매도유효호가건수        |          |
| askStep1BstordCnt  | number(11) | 매도1단계우선호가건수     |          |
| askStep2BstordCnt  | number(11) | 매도2단계우선호가건수     |          |
| askStep1BstordCnt  | number(11) | 매도3단계우선호가건수     |          |
| askStep1BstordCnt  | number(11) | 매도4단계우선호가건수     |          |
| askStep1BstordCnt  | number(11) | 매도5단계우선호가건수     |          |
| ordAcptTm          | number(11) | 호가접수시각          | HHMMSSmm |
| deemTrdPrc         | number(11) | 예상체결가격          |          |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/derivative/futures/kospi200/K2FA001/orderbook'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "101S6000",
        "askStep1BstordPrc": 352.05,
        "askStep2BstordPrc": 352.1,
        "askStep3BstordPrc": 352.15,
        "askStep4BstordPrc": 352.2,
        "askStep5BstordPrc": 352.25,
        "askStep1BstordRqty": 48,
        "askStep2BstordRqty": 132,
        "askStep3BstordRqty": 183,
        "askStep4BstordRqty": 255,
        "askStep5BstordRqty": 140,
        "bidStep1BstordPrc": 352,
        "bidStep2BstordPrc": 351.95,
        "bidStep3BstordPrc": 351.9,
        "bidStep4BstordPrc": 351.85,
        "bidStep5BstordPrc": 351.8,
        "bidStep1BstordRqty": 93,
        "bidStep2BstordRqty": 214,
        "bidStep3BstordRqty": 168,
        "bidStep4BstordRqty": 143,
        "bidStep5BstordRqty": 166,
        "askTotOrdRqty": 16817,
        "bidTotOrdRqty": 15742,
        "askStep1BstordCnt": 27,
        "bidStep1BstordCnt": 33,
        "askStep2BstordCnt": 56,
        "bidStep2BstordCnt": 52,
        "askStep3BstordCnt": 75,
        "bidStep3BstordCnt": 62,
        "askStep4BstordCnt": 70,
        "bidStep4BstordCnt": 60,
        "askStep5BstordCnt": 53,
        "bidStep5BstordCnt": 55,
        "askValidOrdCnt": 3037,
        "bidValidOrdCnt": 2568,
        "ordAcptTm": 10524400,
        "deemTrdPrc": 353.25
    }
}
```



## 상품/지수 선물 투자자별 매매동향 API  <a href="#api" id="api"></a>

* 상품/지수선물 시장별 실시간(30초) 투자자별 매매동향
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/futures/{marketcode}/market/investors" method="get" summary="/v3/market/realtime/derivative/futures/{marketcode}/market/investors" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "10565200",
        "invstLists": [
            {
                "invstCd": "01",
                "MktAccAskTrdvol": 21684,
                "MktAccAskTrdval": 1911484537,
                "MktAccBidTrdvol": 20698,
                "MktAccBidTrdval": 1824368100
            },
            {
                "invstCd": "02",
                "MktAccAskTrdvol": 205,
                "MktAccAskTrdval": 18095087,
                "MktAccBidTrdvol": 194,
                "MktAccBidTrdval": 17129725
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**        | **Type**   | **Description** |           |
| --------------- | ---------- | --------------- | --------- |
| Tm              | string(8)  | 장시간             | HHMMSSmm  |
| invstLists      | array(4)   | 투자자리스트          |           |
| invstCd         | string(4)  | 투자자코드           | 투자자코드표 참조 |
| MktAccAskTrdvol | number(11) | 시장누적매도체결수량      |           |
| MktAccAskTrdval | number(11) | 시장누적매도거래대금      | 백만        |
| MktAccBidTrdvol | number(11) | 시장누적매수체결수량      |           |
| MktAccBidTrdval | number(11) | 시장누적매수거래대금      | 백만        |



#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/derivative/futures/kospi200/market/investors'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "10565200",
        "invstLists": [
            {
                "invstCd": "01",
                "MktAccAskTrdvol": 21684,
                "MktAccAskTrdval": 1911484537,
                "MktAccBidTrdvol": 20698,
                "MktAccBidTrdval": 1824368100
            },
            {
                "invstCd": "02",
                "MktAccAskTrdvol": 205,
                "MktAccAskTrdval": 18095087,
                "MktAccBidTrdvol": 194,
                "MktAccBidTrdval": 17129725
            }
        ]
    }
}
```



## 상품/지수 선물 일중 API  <a href="#api" id="api"></a>

* 상품/지수선물 일중 데이터 제공 \[10초, 1분, 10분단위 시/고/저/종]
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/futures/{marketcode}/{issuecode}/intraday" method="get" summary="/v3/market/realtime/derivative/futures/{marketcode}/{issuecode}/intraday" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) K2FA001
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inddCycleTpCd" required="true" %}
일중 전송주기 구분코드(10:10초, 60:1분, 600:10분)
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
        "isuSrtCd": "K2FA001",
        "hisLists": [
            {
                "inddTm": "12000000",
                "inddOpnprc": 352.45,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.5,
                "inddTrdvol": 2415,
                "inddTrdval": 212761550000,
                "inddAccTrdvol": 130942,
                "inddAccTrdval": 11509201325000
            },
            {
                "inddTm": "11500000",
                "inddOpnprc": 352.4,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.4,
                "inddTrdvol": 2325,
                "inddTrdval": 204814125000,
                "inddAccTrdvol": 128527,
                "inddAccTrdval": 11296439775000
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**      | **Type**   | **Description** |                               |
| ------------- | ---------- | --------------- | ----------------------------- |
| isuSrtCd      | String(9)  | 종목단축코드          | 예) KR7000660001 → 000660&#xD; |
| isuNm         | String(80) | 종목명             |                               |
| hisLists      | Array(4)   | 과거리스트           |                               |
| inddTm        | string(8)  | 일중시간            | HH:MM:SS                      |
| inddOpnprc    | number(11) | 일중시가            | 일중데이타(10초, 1분, 10분)           |
| inddHgprc     | number(11) | 일중고가            | 일중데이타(10초, 1분, 10분)           |
| inddLwprc     | number(11) | 일중저가            | 일중데이타(10초, 1분, 10분)           |
| inddClsprc    | number(11) | 일중종가            | 일중데이타(10초, 1분, 10분)           |
| inddTrdvol    | number(11) | 일중거래량           | 일중데이타(10초, 1분, 10분)           |
| inddTrdval    | number(11) | 일중거래대금          | 일중데이타(10초, 1분, 10분)           |
| inddAccTrdvol | number(11) | 일중누적거래량         |                               |
| inddAccTrdval | number(11) | 일중누적대금          |                               |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/derivative/futures/kospi200/K2FA001/intraday?inddCycleTpCd=600&inqStrtDd=20220530&strtTm=0900&endTm=1200'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "K2FA001",
        "hisLists": [
            {
                "inddTm": "12000000",
                "inddOpnprc": 352.45,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.5,
                "inddTrdvol": 2415,
                "inddTrdval": 212761550000,
                "inddAccTrdvol": 130942,
                "inddAccTrdval": 11509201325000
            },
            {
                "inddTm": "11500000",
                "inddOpnprc": 352.4,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.4,
                "inddTrdvol": 2325,
                "inddTrdval": 204814125000,
                "inddAccTrdvol": 128527,
                "inddAccTrdval": 11296439775000
            }
        ]
    }
}
```



## 상품/지수 옵션 체결 API  <a href="#api" id="api"></a>

* 데이터 발생시마다 실시간 제공
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/options/{marketcode}/{issuecode}/price" method="get" summary="/v3/market/realtime/derivative/options/{marketcode}/{issuecode}/price" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 201S6212
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "201S6212*006",
        "trdPrc": 138.1,
        "opnprc": 138.1,
        "hgprc": 138.1,
        "lwprc": 138.1,
        "accTrdvol": 0,
        "trdTm": 31000000,
        "trdvol": 0,
        "lstTrdTpCd": 0,
        "accTrdval": 0,
        "isuCd": "KR4201S62127",
        "negoBlkAccTrdvol": 0,
        "realtmUplmtprc": 166.1,
        "realtmLwlmtprc": 110.05
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**         | **Type**   | **Description** |                                   |
| ---------------- | ---------- | --------------- | --------------------------------- |
| isuSrtCd         | string(12) | 종목단축코드          | 표준코드&#xD;                         |
| trdPrc           | number(11) | 체결가격            |                                   |
| trdvol           | number(10) | 체결수량, 거래량       | 단위:주                              |
| trdTm            | string(8)  | 체결시각,거래시각       | 테이블 하단 참조                         |
| opnprc           | number(11) | 시가              | 단위:원                              |
| hgprc            | number(11) | 고가              | 단위:원                              |
| lwprc            | number(11) | 저가              | 단위:원                              |
| accTrdvol        | number(12) | 누적체결수량,누적거래량    | 일반체결수량+협의대량체결수량                   |
| accTrdval        | number(22) | 누적거래대금          | 일반체결대금+협의대량체결대금 (단위:원)            |
| negoBlkAccTrdvol | number(12) | 협의대량누적체결수량      |                                   |
| lstAskbidTpCd    | string(1)  | 최종매도매수구분코드      | 1:매도, 2:매수 (최종으로 들어온 호가의 매도매수구분값) |
| realtmUplmtprc   | number(11) | 실시간상한가          |                                   |
| realtmLwlmtprc   | number(11) | 실시간하한가          |                                   |

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
'https://testoap.k-mydata.org/v3/market/realtime/derivative/options/kospi200/201S6212/price'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "201S6212*006",
        "trdPrc": 138.1,
        "opnprc": 138.1,
        "hgprc": 138.1,
        "lwprc": 138.1,
        "accTrdvol": 0,
        "trdTm": 31000000,
        "trdvol": 0,
        "lstTrdTpCd": 0,
        "accTrdval": 0,
        "isuCd": "KR4201S62127",
        "negoBlkAccTrdvol": 0,
        "realtmUplmtprc": 166.1,
        "realtmLwlmtprc": 110.05
    }
}
```



## 상품/지수 옵션 우선호가 API  <a href="#api" id="api"></a>

* 데이터 발생시마다 실시간 제공
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/options/{marketcode}/{issuecode}/orderbook" method="get" summary="/v3/market/realtime/derivative/options/{marketcode}/{issuecode}/orderbook" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 201S6210
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "201S6210",
        "askStep1BstordPrc": 168.6,
        "askStep2BstordPrc": 0,
        "askStep3BstordPrc": 0,
        "askStep4BstordPrc": 0,
        "askStep5BstordPrc": 0,
        "askStep1BstordRqty": 10,
        "askStep2BstordRqty": 0,
        "askStep3BstordRqty": 0,
        "askStep4BstordRqty": 0,
        "askStep5BstordRqty": 0,
        "bidStep1BstordPrc": 112.55,
        "bidStep2BstordPrc": 0,
        "bidStep3BstordPrc": 0,
        "bidStep4BstordPrc": 0,
        "bidStep5BstordPrc": 0,
        "bidStep1BstordRqty": 10,
        "bidStep2BstordRqty": 0,
        "bidStep3BstordRqty": 0,
        "bidStep4BstordRqty": 0,
        "bidStep5BstordRqty": 0,
        "askTotOrdRqty": 10,
        "bidTotOrdRqty": 10,
        "askStep1BstordCnt": 1,
        "bidStep1BstordCnt": 1,
        "askStep2BstordCnt": 0,
        "bidStep2BstordCnt": 0,
        "askStep3BstordCnt": 0,
        "bidStep3BstordCnt": 0,
        "askStep4BstordCnt": 0,
        "bidStep4BstordCnt": 0,
        "askStep5BstordCnt": 0,
        "bidStep5BstordCnt": 0,
        "askValidOrdCnt": 1,
        "bidValidOrdCnt": 1,
        "ordAcptTm": 9000400,
        "deemTrdPrc": 0
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**           | **Type**   | **Description** |          |
| ------------------ | ---------- | --------------- | -------- |
| isuSrtCd           | String(12) | 종목단축코드          |          |
| bidTotOrdRqty      | number(12) | 매수총호가잔량         |          |
| bidStep1BstordPrc  | number(11) | 매수1단계우선호가가격     |          |
| bidStep1BstordRqty | number(12) | 매수1단계우선호가잔량     |          |
| bidStep2BstordPrc  | number(11) | 매수2단계우선호가가격     |          |
| bidStep2BstordRqty | number(12) | 매수2단계우선호가잔량     |          |
| bidStep3BstordPrc  | number(11) | 매수3단계우선호가가격     |          |
| bidStep3BstordRqty | number(12) | 매수3단계우선호가잔량     |          |
| bidStep4BstordPrc  | number(11) | 매수4단계우선호가가격     |          |
| bidStep4BstordRqty | number(12) | 매수4단계우선호가잔량     |          |
| bidStep5BstordPrc  | number(11) | 매수5단계우선호가가격     |          |
| bidStep5BstordRqty | number(12) | 매수5단계우선호가잔량     |          |
| askTotOrdRqty      | number(12) | 매도총호가잔량         |          |
| askStep1BstordPrc  | number(11) | 매도1단계우선호가가격     |          |
| askStep1BstordRqty | number(12) | 매도1단계우선호가잔량     |          |
| askStep2BstordPrc  | number(11) | 매도2단계우선호가가격     |          |
| askStep2BstordRqty | number(12) | 매도2단계우선호가잔량     |          |
| askStep3BstordPrc  | number(11) | 매도3단계우선호가가격     |          |
| askStep3BstordRqty | number(12) | 매도3단계우선호가잔량     |          |
| askStep4BstordPrc  | number(11) | 매도4단계우선호가가격     |          |
| askStep4BstordRqty | number(12) | 매도4단계우선호가잔량     |          |
| askStep5BstordPrc  | number(11) | 매도5단계우선호가가격     |          |
| askStep5BstordRqty | number(12) | 매도5단계우선호가잔량     |          |
| bidValidOrdCnt     | number(11) | 매수유효호가건수        |          |
| bidStep1BstordCnt  | number(11) | 매수1단계우선호가건수     |          |
| bidStep2BstordCnt  | number(11) | 매수2단계우선호가건수     |          |
| bidStep3BstordCnt  | number(11) | 매수3단계우선호가건수     |          |
| bidStep4BstordCnt  | number(11) | 매수4단계우선호가건수     |          |
| bidStep5BstordCnt  | number(11) | 매수5단계우선호가건수     |          |
| askValidOrdCnt     | number(11) | 매도유효호가건수        |          |
| askStep1BstordCnt  | number(11) | 매도1단계우선호가건수     |          |
| askStep2BstordCnt  | number(11) | 매도2단계우선호가건수     |          |
| askStep1BstordCnt  | number(11) | 매도3단계우선호가건수     |          |
| askStep1BstordCnt  | number(11) | 매도4단계우선호가건수     |          |
| askStep1BstordCnt  | number(11) | 매도5단계우선호가건수     |          |
| ordAcptTm          | number(11) | 호가접수시각          | HHMMSSmm |
| deemTrdPrc         | number(11) | 예상체결가격          |          |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/derivative/options/kospi200/201S6210/orderbook'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "201S6210",
        "askStep1BstordPrc": 168.6,
        "askStep2BstordPrc": 0,
        "askStep3BstordPrc": 0,
        "askStep4BstordPrc": 0,
        "askStep5BstordPrc": 0,
        "askStep1BstordRqty": 10,
        "askStep2BstordRqty": 0,
        "askStep3BstordRqty": 0,
        "askStep4BstordRqty": 0,
        "askStep5BstordRqty": 0,
        "bidStep1BstordPrc": 112.55,
        "bidStep2BstordPrc": 0,
        "bidStep3BstordPrc": 0,
        "bidStep4BstordPrc": 0,
        "bidStep5BstordPrc": 0,
        "bidStep1BstordRqty": 10,
        "bidStep2BstordRqty": 0,
        "bidStep3BstordRqty": 0,
        "bidStep4BstordRqty": 0,
        "bidStep5BstordRqty": 0,
        "askTotOrdRqty": 10,
        "bidTotOrdRqty": 10,
        "askStep1BstordCnt": 1,
        "bidStep1BstordCnt": 1,
        "askStep2BstordCnt": 0,
        "bidStep2BstordCnt": 0,
        "askStep3BstordCnt": 0,
        "bidStep3BstordCnt": 0,
        "askStep4BstordCnt": 0,
        "bidStep4BstordCnt": 0,
        "askStep5BstordCnt": 0,
        "bidStep5BstordCnt": 0,
        "askValidOrdCnt": 1,
        "bidValidOrdCnt": 1,
        "ordAcptTm": 9000400,
        "deemTrdPrc": 0
    }
}
```



## 상품/지수 옵션 투자자별 매매동향 API  <a href="#api" id="api"></a>

* 상품/지수 옵션 시장별 실시간(30초) 투자자별 매매동향
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/options/{marketcode}/market/investors" method="get" summary="/v3/market/realtime/derivative/options/{marketcode}/market/investors" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "9000400",
        "invstLists": [
            {
                "invstCd": "01",
                "CallAccAskTrdvol": 136966,
                "CallAccAskTrdval": 8611687,
                "CallAccBidTrdvol": 108712,
                "CallAccBidTrdval": 7938542,
                "PutAccAskTrdvol": 124135,
                "PutAccAskTrdval": 8736282,
                "PutAccBidTrdvol": 92749,
                "PutAccBidTrdval": 10380110
            },
            {
                "invstCd": "02",
                "CallAccAskTrdvol": 0,
                "CallAccAskTrdval": 0,
                "CallAccBidTrdvol": 0,
                "CallAccBidTrdval": 0,
                "PutAccAskTrdvol": 0,
                "PutAccAskTrdval": 0,
                "PutAccBidTrdvol": 0,
                "PutAccBidTrdval": 0
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**         | **Type**   | **Description** |           |
| ---------------- | ---------- | --------------- | --------- |
| Tm               | string(8)  | 장시간             | HHMMSSmm  |
| invstLists       | array(4)   | 투자자리스트          |           |
| invstCd          | string(4)  | 투자자코드           | 투자자코드표 참조 |
| CallAccAskTrdvol | number(11) | 옵션콜누적매도체결수량     |           |
| CallAccAskTrdval | number(11) | 옵션콜누적매도거래대금     | 백만        |
| CallAccBidTrdvol | number(11) | 옵션콜누적매수체결수량     |           |
| CallAccBidTrdval | number(11) | 옵션콜누적매수거래대금     | 백만        |
| PutAccAskTrdvol  | number(11) | 옵션풋누적매도체결수량     |           |
| PutAccAskTrdval  | number(11) | 옵션풋누적매도거래대금     | 백만        |
| PutAccBidTrdvol  | number(11) | 옵션풋누적매수체결수량     |           |
| PutAccBidTrdval  | number(11) | 옵션풋누적매수거래대금     | 백만        |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/derivative/options/kospi200/market/investors'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "Tm": "9000400",
        "invstLists": [
            {
                "invstCd": "01",
                "CallAccAskTrdvol": 136966,
                "CallAccAskTrdval": 8611687,
                "CallAccBidTrdvol": 108712,
                "CallAccBidTrdval": 7938542,
                "PutAccAskTrdvol": 124135,
                "PutAccAskTrdval": 8736282,
                "PutAccBidTrdvol": 92749,
                "PutAccBidTrdval": 10380110
            },
            {
                "invstCd": "02",
                "CallAccAskTrdvol": 0,
                "CallAccAskTrdval": 0,
                "CallAccBidTrdvol": 0,
                "CallAccBidTrdval": 0,
                "PutAccAskTrdvol": 0,
                "PutAccAskTrdval": 0,
                "PutAccBidTrdvol": 0,
                "PutAccBidTrdval": 0
            }
        ]
    }
}
```



## 상품/지수 옵션 일중 API  <a href="#api" id="api"></a>

* 상품/지수 옵션 일중 데이터 제공 \[10초, 1분, 10분단위 시/고/저/종]
* 제공시간 : 실시간

{% swagger baseUrl="https://{APIGWAddr}/v3/market/realtime/derivative" path="/options/{marketcode}/{issuecode}/intraday" method="get" summary="/v3/market/realtime/derivative/options/{marketcode}/{issuecode}/intraday" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" required="true" %}
ex) 201S6210
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inddCycleTpCd" required="true" %}
일중 전송주기 구분코드(10:10초, 60:1분, 600:10분)
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
        "isuSrtCd": "201S6210",
        "hisLists": [
            {
                "inddTm": "12000000",
                "inddOpnprc": 352.45,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.5,
                "inddTrdvol": 2415,
                "inddTrdval": 212761550000,
                "inddAccTrdvol": 130942,
                "inddAccTrdval": 11509201325000
            },
            {
                "inddTm": "11500000",
                "inddOpnprc": 352.4,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.4,
                "inddTrdvol": 2325,
                "inddTrdval": 204814125000,
                "inddAccTrdvol": 128527,
                "inddAccTrdval": 11296439775000
            }
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**      | **Type**   | **Description** |                               |
| ------------- | ---------- | --------------- | ----------------------------- |
| isuSrtCd      | String(9)  | 종목단축코드          | 예) KR7000660001 → 000660&#xD; |
| isuNm         | String(80) | 종목명             |                               |
| hisLists      | Array(4)   | 과거리스트           |                               |
| inddTm        | string(8)  | 일중시간            | HH:MM:SS                      |
| inddOpnprc    | number(11) | 일중시가            | 일중데이타(10초, 1분, 10분)           |
| inddHgprc     | number(11) | 일중고가            | 일중데이타(10초, 1분, 10분)           |
| inddLwprc     | number(11) | 일중저가            | 일중데이타(10초, 1분, 10분)           |
| inddClsprc    | number(11) | 일중종가            | 일중데이타(10초, 1분, 10분)           |
| inddTrdvol    | number(11) | 일중거래량           | 일중데이타(10초, 1분, 10분)           |
| inddTrdval    | number(11) | 일중거래대금          | 일중데이타(10초, 1분, 10분)           |
| inddAccTrdvol | number(11) | 일중누적거래량         |                               |
| inddAccTrdval | number(11) | 일중누적대금          |                               |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/realtime/derivative/options/kospi200/201S6210/intraday?inddCycleTpCd=600&inqStrtDd=20220530&strtTm=0900&endTm=1200'
```

#### Response Example

```yaml
{
    "jsonrpc": "2.0",
    "result": {
        "isuSrtCd": "201S6210",
        "hisLists": [
            {
                "inddTm": "12000000",
                "inddOpnprc": 352.45,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.5,
                "inddTrdvol": 2415,
                "inddTrdval": 212761550000,
                "inddAccTrdvol": 130942,
                "inddAccTrdval": 11509201325000
            },
            {
                "inddTm": "11500000",
                "inddOpnprc": 352.4,
                "inddHgprc": 352.5,
                "inddLwprc": 352.25,
                "inddClsprc": 352.4,
                "inddTrdvol": 2325,
                "inddTrdval": 204814125000,
                "inddAccTrdvol": 128527,
                "inddAccTrdval": 11296439775000
            }
        ]
    }
}
```





