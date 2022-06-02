# 파생실시간종가A

상품/지수 선물시장과 옵션시장에 상장된 종목 리스트, 종목 마스터 등 종가 정보를 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

## 상품/지수 선물 종목 리스트 API  <a href="#api" id="api"></a>

* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/derivative" path="/futures/{marketcode}/lists" method="get" summary="/v3/market/closed/derivative/futures/{marketcode}/lists" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
    "trdDd": "20220602",
    "mktEndTm": "1550",
    "isuLists": [
        {
            "isuSrtCd": "101S6000",
            "isuCd": "KR4101S60008",
            "isuKorNm": "KOSPI200 선물 2206",
            "isuKorAbbr": "K200 선물 2206",
            "map_to": "101S6000*005"
        },
        {
            "isuSrtCd": "K2FA001",
            "isuCd": "KR4101S60008",
            "isuKorNm": "KOSPI200 선물 2206",
            "isuKorAbbr": "K200 선물 2206",
            "map_to": "K2FA001"
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**    | **Type**   | **Description**  |                             |
| ----------- | ---------- | ---------------- | --------------------------- |
| trdDd       | String(8)  | 체결일자, 거래일자, 매매일자 | YYYYMMDD                    |
| isuLists    | Array(4)   | 종목리스트            |                             |
| isuCd       | String(12) | 종목코드             | 표준코드                        |
| isuSrtCd    | String(9)  | 종목단축코드           | 예) KR4101C90009 → K101C9000 |
| isuKorNm    | String(80) | 종목한글명            |                             |
| isuKorAbbrv | String(40) | 종목한글약명           | 가나다                         |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/derivative/futures/kospi200/lists'
```

#### Response Example

```yaml
{
    "trdDd": "20220602",
    "mktEndTm": "1550",
    "isuLists": [
        {
            "isuSrtCd": "101S6000",
            "isuCd": "KR4101S60008",
            "isuKorNm": "KOSPI200 선물 2206",
            "isuKorAbbr": "K200 선물 2206",
            "map_to": "101S6000*005"
        },
        {
            "isuSrtCd": "K2FA001",
            "isuCd": "KR4101S60008",
            "isuKorNm": "KOSPI200 선물 2206",
            "isuKorAbbr": "K200 선물 2206",
            "map_to": "K2FA001"
        }
    ]
}
```

## 상품/지수 선물 종목 마스터 API  <a href="#api" id="api"></a>

* 선물 종목에 대한 기초 자료 제공
* 제공시간 : AM 06:30

{% swagger baseUrl="https://{APIGWAddr}/v3/market/closed/derivative" path="/futures/{marketcode}/{issuecode}/master" method="get" summary="/v3/market/closed/derivative/futures/{marketcode}/{issuecode}/master" %}
{% swagger-description %}
종목리스트
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" required="true" %}
ex) kospi200
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="issuecode" %}
ex) 101S6000
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
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
        "prevddClsprc": 354.15,
        "prevddOpnprc": 352.4,
        "prevddHgprc": 354.6,
        "prevddLwprc": 350.25,
        "prevddAccTrdvol": 240692,
        "prevddAccTrdval": 21215619325000,
        "prevddOpnintQty": 292368,
        "setlPrcTheoPrcDivrgRt": -0.19,
        "trdDd": 20220602,
        "basPrc": 354.15,
        "isuKorNm": "KOSPI200 선물 2206",
        "isuKorAbbrv": "K200 선물 2206",
        "isuCd": "KR4101S60008",
        "listDd": 20200612,
        "remainDys": 8,
        "cdInt": 1.96,
        "lsttrdDd": 20220609,
        "expDd": 202206,
        "ulyId": "KOSPI200",
        "prcLmtStep1Uplmtprc": 382.45,
        "prcLmtStep2Uplmtprc": 407.25,
        "prcLmtStep3Uplmtprc": 424.95,
        "prcLmtStep1Lwlmtprc": 325.85,
        "prcLmtStep2Lwlmtprc": 301.05,
        "prcLmtStep3Lwlmtprc": 283.35,
        "opnintLmtQty": null,
        "setlmult": 250000,
        "setlTheoPrc": null,
        "basTheoPrc": null
    }
}
```
{% endswagger-response %}
{% endswagger %}

#### Response Parameters

| **Name**              | **Type**   | **Description**  | ​                                                                            |
| --------------------- | ---------- | ---------------- | ---------------------------------------------------------------------------- |
| trdDd                 | string(8)  | 체결일자, 거래일자, 매매일자 | YYYYMMDD                                                                     |
| isuCd                 | string(12) | 종목코드             | ​                                                                            |
| isuSrtCd              | string(9)  | 종목단축코드           | 예) KR4101C90009 → K101C9000                                                  |
| isuKorNm              | string(80) | 종목한글명            |                                                                              |
| isuKorAbbrv           | string(40) | 종목한글약명           | 가나다                                                                          |
| listDd                | string(8)  | 상장일자             | YYYYMMDD                                                                     |
| prcLmtStep1Uplmtprc   | number(12) | 가격제한1단계상한가       |                                                                              |
| prcLmtStep1Lwlmtprc   | number(12) | 가격제한1단계하한가       |                                                                              |
| prcLmtStep2Uplmtprc   | number(12) | 가격제한2단계상한가       |                                                                              |
| prcLmtStep2Lwlmtprc   | number(12) | 가격제한2단계하한가       |                                                                              |
| prcLmtStep3Uplmtprc   | number(12) | 가격제한3단계상한가       |                                                                              |
| prcLmtStep3Lwlmtprc   | number(12) | 가격제한3단계하한가       |                                                                              |
| basPrc                | number(11) | 기준가격,기준가액        |                                                                              |
| ulyId                 | string(3)  | 기초자산명            |                                                                              |
| lsttrdDd              | string(8)  | 최종거래일자           |                                                                              |
| expDd                 | string(8)  | 만기년월             | 권리행사 가능한 만기년월                                                                |
| setlmult              | number(22) | 거래승수             | 약정대금 및 결제시 사용하는 계산승수                                                         |
| remainDys             | number(8)  | 잔존일수             |                                                                              |
| setlTheoPrc           | number(16) | 정산이론가격           |                                                                              |
| basTheoPrc            | number(16) | 기준이론가격           |                                                                              |
| prevddClsprc          | number(11) | 전일종가             |                                                                              |
| prevddOpnprc          | number(11) | 전일시가             |                                                                              |
| prevddHgprc           | number(11) | 전일고가             |                                                                              |
| prevddLwprc           | number(11) | 전일저가             |                                                                              |
| setlPrcTheoPrcDivrgRt | number(13) | 정산가격이론가격괴리율      |                                                                              |
| prevddOpnintQty       | number(12) | 전일미결제약정수량        |                                                                              |
| inlistHgstprc         | number(11) | 상장중최고가           |                                                                              |
| inlistLwstprc         | number(11) | 상장중최저가           |                                                                              |
| midyyHgstprc          | number(11) | 연중최고가            |                                                                              |
| midyyLwstprc          | number(11) | 연중최저가            |                                                                              |
| inlistHgstprcDd       | string(8)  | 상장중최고가일자         |                                                                              |
| inlistLwstprcDd       | string(8)  | 상장중최저가일자         |                                                                              |
| midyyHgstprcDd        | string(8)  | 연중최고가일자          |                                                                              |
| midyyLwstprcDd        | string(8)  | 연중최저가일자          |                                                                              |
| prevddAccTrdvol       | number(15) | 전일체결수량,전일거래량     |                                                                              |
| prevddAccTrdval       | number(22) | 전일거래대금           |                                                                              |
| cdInt                 | number(7)  | CD금리             | 예) 999.999                                                                   |
| opnintLmtQty          | number(15) | 미결제한도수량          | <p>*적용일에 적용되는 상품의 계좌별  미결제 한도 계약수.  미결제 한도가 적용되지 않은 상품은 0<br>* 주식선물에만 해당</p> |

#### Request Example  <a href="#request-body-example" id="request-body-example"></a>

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://testoap.k-mydata.org/v3/market/closed/derivative/futures/kospi200/101S6000/master'
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
        "prevddClsprc": 354.15,
        "prevddOpnprc": 352.4,
        "prevddHgprc": 354.6,
        "prevddLwprc": 350.25,
        "prevddAccTrdvol": 240692,
        "prevddAccTrdval": 21215619325000,
        "prevddOpnintQty": 292368,
        "setlPrcTheoPrcDivrgRt": -0.19,
        "trdDd": 20220602,
        "basPrc": 354.15,
        "isuKorNm": "KOSPI200 선물 2206",
        "isuKorAbbrv": "K200 선물 2206",
        "isuCd": "KR4101S60008",
        "listDd": 20200612,
        "remainDys": 8,
        "cdInt": 1.96,
        "lsttrdDd": 20220609,
        "expDd": 202206,
        "ulyId": "KOSPI200",
        "prcLmtStep1Uplmtprc": 382.45,
        "prcLmtStep2Uplmtprc": 407.25,
        "prcLmtStep3Uplmtprc": 424.95,
        "prcLmtStep1Lwlmtprc": 325.85,
        "prcLmtStep2Lwlmtprc": 301.05,
        "prcLmtStep3Lwlmtprc": 283.35,
        "opnintLmtQty": null,
        "setlmult": 250000,
        "setlTheoPrc": null,
        "basTheoPrc": null
    }
}
```











