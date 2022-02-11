# 업종 지수

KOSPI/KOSDAQ등의 지수 예상지수 및 업종별 투자자별 거래량등을 제공한다.

## Syntax

HTTP methods | **GET**

Authentication | **API Key**

{% hint style="success" %}
`marketcode` 및 `issuecode` 는 [코드표 > "시장코드표"](https://koscom.gitbook.io/open-api/api/market/codetable)를 참조하세요.
{% endhint %}

{% hint style="info" %}
업종지수 스트리밍 조회는 xx를 참고하세요.
{% endhint %}

## 업종 종가

{% swagger baseUrl="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/closeprice" method="get" summary="/v2/market/index/{marketcode}/{issuecode}/closeprice" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" type="string" %}
시장코드
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" type="string" %}
업종코드 ex) K1
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "isuCnt": 891,
     "trdPrc": 2409.03,
     "cmpprevddTpCd": "5",
     "opnprc": 2446.81,
     "hgprc": 2449.88,
     "lwprc": 2399.58,
     "accTrdvol": 575922,
     "accTrdval": 8999465,
     "mktcap": 1609052294,
     "cmpprevddPrc": -48.22,
     "listShrs": 53713300 
  } 
}
```
{% endswagger-response %}

{% swagger-response status="400" description="" %}
```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endswagger-response %}
{% endswagger %}

### Response Parameters

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

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/index/kospi/K1/closeindex'
```

### Response Example

```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```

## 업종 지수

{% swagger baseUrl="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/index" method="get" summary="/v2/market/index/{marketcode}/{issuecode}/index" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" type="string" %}
시장코드
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" type="string" %}
업종코드 ex) K1
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "trdPrc": 2469.21,
     "cmpprevddTpCd": "2",
     "accTrdvol": 494710,
     "trdTm": 13063000,
     "accTrdval": 6246486,
     "cmpprevddPrc": 7.83 
  } 
}
```
{% endswagger-response %}
{% endswagger %}

### Response Parameters

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

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/index/kospi/K1/index'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "trdPrc": 2040.04,
     "cmpprevddTpCd": "2",
     "accTrdvol": 114261,
     "trdTm": 10122000,
     "accTrdval": 1075046,
     "cmpprevddPrc": 11.6 
  } 
}
```

## 업종 예상지수

{% swagger baseUrl="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/prospectindex" method="get" summary="/v2/market/index/{marketcode}/{issuecode}/prospectindex" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" type="string" %}
시장코드
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" type="string" %}
업종코드 ex) K1
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "deemTm": "9000000",
     "deemTrdPrc": 2471.12,
     "deemAccTrdvol": 15801,
     "deemcmpprevddPrc": 9.74,
     "deemcmpprevddTpCd": "69",
     "deemAccTrdval": 298225 
  } 
}
```
{% endswagger-response %}
{% endswagger %}

### Response Parameters

| **Name**          | **Type**   | **Description** |                                                      |
| ----------------- | ---------- | --------------- | ---------------------------------------------------- |
| isuSrtCd          | String(3)  | 업종코드            | 업종코드표 참조                                             |
| deemTm            | String(8)  | 예상체결시각          | HHMMSSmm                                             |
| deemTrdPrc        | number(10) | 예상지수            |                                                      |
| deemcmpprevddTpCd | String(1)  | 예상전일대비구분코드      | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| deemcmpprevddPrc  | number(11) | 예상전일대비지수        |                                                      |
| deemAccTrdvol     | number(12) | 예상누적체결수량        | 단위:주                                                 |
| deemAccTrdval     | number(22) | 예상누적거래대금        | 단위:원                                                 |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/index/kospi/K1/prospectindex'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "deemTm": "9000000",
     "deemTrdPrc": 2029.95,
     "deemAccTrdvol": 5041,
     "deemcmpprevddPrc": 1.51,
     "deemcmpprevddTpCd": "69",
     "deemAccTrdval": 46703 
  } 
}
```

## 업종 시가총액

{% swagger baseUrl="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/marketcap" method="get" summary="/v2/market/index/{marketcode}/{issuecode}/marketcap" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" type="string" %}
시장코드
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" type="string" %}
업종코드 ex) K1
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "isuCnt": 1442,
     "accTrdvol": 501479,
     "accTrdval": 6323816,
     "listShrs": 53642471 
  } 
}
```
{% endswagger-response %}
{% endswagger %}

### Response Parameters

| **Name**  | **Type**   | **Description** |                         |
| --------- | ---------- | --------------- | ----------------------- |
| isuSrtCd  | String(3)  | 업종코드            |                         |
| isuCnt    | number(16) | 종목수             |                         |
| listShrs  | number(16) | 상장주식수,상장증권수     | 업종상장주식수 단위는  천주, 그외는 1주 |
| accTrdvol | number(12) | 누적체결수량,누적거래량    | 단위:주                    |
| accTrdval | number(22) | 누적거래대금          | 단위:원                    |
| mktcap    | number(22) | 시가총액            | 단위: 업종-백만               |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/index/kospi/K1/marketcap'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "isuCnt": 901,
     "accTrdvol": 115822,
     "accTrdval": 1087268,
     "mktcap": 1342909243,
     "listShrs": 55522062 
  } 
}
```

## 업종별 투자자별

{% swagger baseUrl="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/investors" method="get" summary="/v2/market/index/{marketcode}/{issuecode}/investors" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" type="string" %}
시장코드
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" type="string" %}
업종코드 ex) K1
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "Tm": "0",
     "isuSrtCd": "K1",
     "invstLists": [ 
      {
         "invstCd": "0",
         "askTrdvol": 5907489,
         "askTrdval": 302311797,
         "bidTrdvol": 6739796,
         "bidTrdval": 381023826 
      },
      {
         "invstCd": "0",
         "askTrdvol": 2065869,
         "askTrdval": 96146505,
         "bidTrdvol": 2982361,
         "bidTrdval": 122971912 
      },
      ... 이하생략 ...
    ] 
  } 
}
```
{% endswagger-response %}
{% endswagger %}

### Response Parameters

| **Name**   | **Type**   | **Description** |             |
| ---------- | ---------- | --------------- | ----------- |
| Tm         | string(8)  | 장시간             | HHMMSSmm    |
| invstLists | Array(4)   | 투자자리스트          |             |
| invstCd    | string(4)  | 투자자코드           | '투자자코드표' 참조 |
| askTrdvol  | number(10) | 매도체결수량,매도거래량    |             |
| askTrdval  | number(22) | 매도거래대금          |             |
| bidTrdvol  | number(10) | 매수체결수량,매수거래량    |             |
| bidTrdval  | number(22) | 매수거래대금          |             |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/index/kospi/K1/investors'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "Tm": "10143000",
     "isuSrtCd": "K1",
     "invstLists": [ 
      {
         "invstCd": "01",
         "askTrdvol": 1807478,
         "askTrdval": 83095436,
         "bidTrdvol": 1075480,
         "bidTrdval": 45434170 
      },

      {
         "invstCd": "02",
         "askTrdvol": 122629,
         "askTrdval": 6850362,
         "bidTrdvol": 254701,
         "bidTrdval": 11994572 
      },

      {
         "invstCd": "03",
         "askTrdvol": 566249,
         "askTrdval": 14767548,
         "bidTrdvol": 447322,
         "bidTrdval": 17725585 
      },

      {
         "invstCd": "04",
         "askTrdvol": 112269,
         "askTrdval": 2741904,
         "bidTrdvol": 10007,
         "bidTrdval": 543139 
      },

      {
         "invstCd": "05",
         "askTrdvol": 2372,
         "askTrdval": 156234,
         "bidTrdvol": 11671,
         "bidTrdval": 487228 
      },

      {
         "invstCd": "06",
         "askTrdvol": 1278442,
         "askTrdval": 54405488,
         "bidTrdvol": 1153817,
         "bidTrdval": 54565514 
      },

      {
         "invstCd": "07",
         "askTrdvol": 0,
         "askTrdval": 0,
         "bidTrdvol": 0,
         "bidTrdval": 0 
      },

      {
         "invstCd": "08",
         "askTrdvol": 4246576,
         "askTrdval": 181910152,
         "bidTrdvol": 3331688,
         "bidTrdval": 149146888 
      },

      {
         "invstCd": "09",
         "askTrdvol": 1461253,
         "askTrdval": 15613019,
         "bidTrdvol": 497067,
         "bidTrdval": 9715010 
      },

      {
         "invstCd": "10",
         "askTrdvol": 99655391,
         "askTrdval": 681510822,
         "bidTrdvol": 99692222,
         "bidTrdval": 690983059 
      },

      {
         "invstCd": "11",
         "askTrdvol": 10024570,
         "askTrdval": 205378931,
         "bidTrdvol": 11866813,
         "bidTrdval": 234567966 
      },

      {
         "invstCd": "12",
         "askTrdvol": 115387790,
         "askTrdval": 1084412924,
         "bidTrdvol": 115387790,
         "bidTrdval": 1084412923 
      },

      {
         "invstCd": "13",
         "askTrdvol": 357137,
         "askTrdval": 19893180,
         "bidTrdvol": 378690,
         "bidTrdval": 18396680 
      },

      {
         "invstCd": "14",
         "askTrdvol": 9792902,
         "askTrdval": 203541449,
         "bidTrdvol": 11574270,
         "bidTrdval": 231474813 
      },

      {
         "invstCd": "15",
         "askTrdvol": 231668,
         "askTrdval": 1837482,
         "bidTrdvol": 292543,
         "bidTrdval": 3093153 
      },

      {
         "invstCd": "16",
         "askTrdvol": 1461253,
         "askTrdval": 15613019,
         "bidTrdvol": 497067,
         "bidTrdval": 9715010 
      } 
    ] 
  } 
}
```

## 업종 일중

{% swagger baseUrl="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/intraday" method="get" summary="/v2/market/index/{marketcode}/{issuecode}/intraday" %}
{% swagger-description %}
상품/지수선물 종목 10초/분별 데이터 제공
{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" type="string" %}
시장코드
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" type="string" %}
업종코드 ex) K1
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inddCycleTpCd" type="string" %}
일중전송주기구분코드 구분코드 (10:10초, 60:1분, 600:10분)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" type="string" %}
조회시작일자 (YYYYMMDD)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="strtTm" type="string" %}
시작시각 (HHMM)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="endTm" type="string" %}
종료시각 (HHMM)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "hisLists": [ 
      {
         "inddTm": "9300000",
         "inddOpnprc": 2386.7,
         "inddHgprc": 2388.88,
         "inddLwprc": 2385.62,
         "inddClsprc": 2387.58,
         "inddTrdvol": 53052 
      },
      {
         "inddTm": "9200000",
         "inddOpnprc": 2387.03,
         "inddHgprc": 2388.37,
         "inddLwprc": 2385.86,
         "inddClsprc": 2386.65,
         "inddTrdvol": 42379 
      },
      {
         "inddTm": "9100000",
         "inddOpnprc": 2386.76,
         "inddHgprc": 2388.33,
         "inddLwprc": 2383.47,
         "inddClsprc": 2387.37,
         "inddTrdvol": 29504 
      } 
    ] 
  } 
}
```
{% endswagger-response %}
{% endswagger %}

### Response Parameters

| **Name**   | **Type**   | **Description** |                     |
| ---------- | ---------- | --------------- | ------------------- |
| isuSrtCd   | String(3)  | 업종코드            | 0                   |
| isuNm      | String(80) | 종목명             |                     |
| hisLists   | Array(4)   | 과거리스트           |                     |
| inddTm     | string(8)  | 일중시간            | HH:MM:SS            |
| inddOpnprc | number(11) | 일중시가            | 일중데이타(10초, 1분, 10분) |
| inddHgprc  | number(11) | 일중고가            | 일중데이타(10초, 1분, 10분) |
| inddLwprc  | number(11) | 일중저가            | 일중데이타(10초, 1분, 10분) |
| inddClsprc | number(11) | 일중종가            | 일중데이타(10초, 1분, 10분) |
| inddTrdvol | number(11) | 일중거래량           | 일중데이타(10초, 1분, 10분) |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/index/kospi/K1/intraday?inddCycleTpCd=600&inqStrtDd=20181228&strtTm=0900&endTm=1500'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "hisLists": [ 
      {
         "inddTm": "10154000",
         "inddOpnprc": 2040.21,
         "inddHgprc": 2041.08,
         "inddLwprc": 2039.65,
         "inddClsprc": 2039.69,
         "inddTrdvol": 117477 
      },

      {
         "inddTm": "10100000",
         "inddOpnprc": 2041.27,
         "inddHgprc": 2041.96,
         "inddLwprc": 2039.75,
         "inddClsprc": 2041.31,
         "inddTrdvol": 111972 
      },

      {
         "inddTm": "10000000",
         "inddOpnprc": 2041.18,
         "inddHgprc": 2042.91,
         "inddLwprc": 2040.1,
         "inddClsprc": 2042.74,
         "inddTrdvol": 102781 
      },

      {
         "inddTm": "9500000",
         "inddOpnprc": 2040.07,
         "inddHgprc": 2041.66,
         "inddLwprc": 2038.86,
         "inddClsprc": 2041.37,
         "inddTrdvol": 89531 
      },

      {
         "inddTm": "9400000",
         "inddOpnprc": 2041.14,
         "inddHgprc": 2044.03,
         "inddLwprc": 2039.16,
         "inddClsprc": 2039.86,
         "inddTrdvol": 74108 
      },

      {
         "inddTm": "9300000",
         "inddOpnprc": 2041.38,
         "inddHgprc": 2041.43,
         "inddLwprc": 2036.83,
         "inddClsprc": 2039.94,
         "inddTrdvol": 60232 
      },

      {
         "inddTm": "9200000",
         "inddOpnprc": 2040.85,
         "inddHgprc": 2041.71,
         "inddLwprc": 2037.96,
         "inddClsprc": 2041.41,
         "inddTrdvol": 48078 
      },

      {
         "inddTm": "9100000",
         "inddOpnprc": 2036.7,
         "inddHgprc": 2043.54,
         "inddLwprc": 2035.41,
         "inddClsprc": 2040.32,
         "inddTrdvol": 31820 
      } 
    ] 
  } 
}
```

## 업종 히스토리

{% swagger baseUrl="https://{APIGWAddr}/v2/market/index" path="/{marketcode}/{issuecode}/history" method="get" summary="/v2/market/index/{marketcode}/{issuecode}/history" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="marketcode" type="string" %}
시장코드
{% endswagger-parameter %}

{% swagger-parameter in="path" name="issuecode" type="string" %}
업종코드 ex) K1
{% endswagger-parameter %}

{% swagger-parameter in="query" name="trnsmCycleTpCd" type="string" %}
전송주기구분코드 (D:일별, W:주별, M:월별)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqStrtDd" type="string" %}
조회시작일자 (YYYYMMDD)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="inqEndDd" type="string" %}
조회종료일자 (YYYYMMDD)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="reqCnt" type="number" %}
요청건수 (최대 100건)
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "hisLists": [ 
      {
         "BzDd": 20170331,
         "trdPrc": 2160.23,
         "cmpprevddTpCd": "5",
         "opnprc": 2166.62,
         "hgprc": 2166.93,
         "lwprc": 2159.8,
         "accTrdvol": 441640,
         "accTrdval": 4479971,
         "cmpprevddPrc": -4.41 
      },

      {
         "BzDd": 20170330,
         "trdPrc": 2164.64,
         "cmpprevddTpCd": "5",
         "opnprc": 2170.18,
         "hgprc": 2174.16,
         "lwprc": 2159.16,
         "accTrdvol": 643563,
         "accTrdval": 4574158,
         "cmpprevddPrc": -2.34 
      } 
    ] 
  } 
}
```
{% endswagger-response %}
{% endswagger %}

### Response Parameters

| **Name**      | **Type**   | **Description** |               |
| ------------- | ---------- | --------------- | ------------- |
| isuSrtCd      | String(3)  | 업종코드            | 코드표 >업종코드표 참조 |
| isuKorNm      | String(80) | 종목한글명           |               |
| hisLists      | Array(4)   | 과거리스트           |               |
| trdDd         | string(8)  | 체결일자,거래일자,매매일자  | YYYYMMDD      |
| trdPrc        | number(11) | 체결가격            |               |
| cmpprevddTpCd | string(1)  | 전일대비부호          |               |
| cmpprevddPrc  | number(11) | 전일대비가격          |               |
| accTrdvol     | number(12) | 누적체결수량,누적거래량    |               |
| accTrdval     | number(22) | 누적거래대금          |               |
| opnprc        | number(11) | 시가              |               |
| hgprc         | number(11) | 고가              |               |
| lwprc         | number(11) | 저가              |               |

### Request Example

```bash
curl --include --header "apikey:l7xx230ef2235e3xxxxxc982eb192ac98e206" \
--request GET \
'https://sandbox-apigw.koscom.co.kr/v2/market/index/kospi/K1/history?trnsmCycleTpCd=D&inqStrtDd=20181001&inqEndDd=20181231&reqCnt=20'
```

### Response Example

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": "K1",
     "hisLists": [ 
      {
         "BzDd": 20181228,
         "trdPrc": 2040.19,
         "cmpprevddTpCd": "2",
         "opnprc": 2036.7,
         "hgprc": 2044.03,
         "lwprc": 2035.41,
         "accTrdvol": 117954,
         "accTrdval": 1105573,
         "cmpprevddPrc": 11.75 
      },

      {
         "BzDd": 20181227,
         "trdPrc": 2028.44,
         "cmpprevddTpCd": "2",
         "opnprc": 2032.09,
         "hgprc": 2035.57,
         "lwprc": 2021.39,
         "accTrdvol": 398021,
         "accTrdval": 5351003,
         "cmpprevddPrc": 0.43 
      },

      {
         "BzDd": 20181226,
         "trdPrc": 2028.01,
         "cmpprevddTpCd": "5",
         "opnprc": 2028.81,
         "hgprc": 2037.83,
         "lwprc": 2014.28,
         "accTrdvol": 321499,
         "accTrdval": 5424078,
         "cmpprevddPrc": -27 
      },

      {
         "BzDd": 20181224,
         "trdPrc": 1945.91,
         "cmpprevddTpCd": "5",
         "opnprc": 2057.35,
         "hgprc": 2057.35,
         "lwprc": 1878.85,
         "accTrdvol": 346,
         "accTrdval": 5788,
         "cmpprevddPrc": -115.58 
      },

      {
         "BzDd": 20181221,
         "trdPrc": 2213.93,
         "cmpprevddTpCd": "2",
         "opnprc": 2064.6,
         "hgprc": 2222.62,
         "lwprc": 2064.6,
         "accTrdvol": 774,
         "accTrdval": 20216,
         "cmpprevddPrc": 153.81 
      },

      {
         "BzDd": 20181220,
         "trdPrc": 2048.37,
         "cmpprevddTpCd": "5",
         "opnprc": 2063.7,
         "hgprc": 2170.26,
         "lwprc": 2047.52,
         "accTrdvol": 1228,
         "accTrdval": 28627,
         "cmpprevddPrc": -30.47 
      },

      {
         "BzDd": 20181219,
         "trdPrc": 2078.84,
         "cmpprevddTpCd": "2",
         "opnprc": 2068.95,
         "hgprc": 2080.65,
         "lwprc": 2063.01,
         "accTrdvol": 418796,
         "accTrdval": 5124894,
         "cmpprevddPrc": 16.73 
      },

      {
         "BzDd": 20181218,
         "trdPrc": 2062.11,
         "cmpprevddTpCd": "5",
         "opnprc": 2057.39,
         "hgprc": 2074.31,
         "lwprc": 2054.26,
         "accTrdvol": 429530,
         "accTrdval": 5241610,
         "cmpprevddPrc": -8.98 
      },

      {
         "BzDd": 20181217,
         "trdPrc": 2071.09,
         "cmpprevddTpCd": "2",
         "opnprc": 2071.21,
         "hgprc": 2075.93,
         "lwprc": 2065.51,
         "accTrdvol": 444522,
         "accTrdval": 4764477,
         "cmpprevddPrc": 1.71 
      },

      {
         "BzDd": 20181214,
         "trdPrc": 2069.38,
         "cmpprevddTpCd": "5",
         "opnprc": 2097.3,
         "hgprc": 2188.68,
         "lwprc": 1972.65,
         "accTrdvol": 448237,
         "accTrdval": 5784241,
         "cmpprevddPrc": -26.17 
      },

      {
         "BzDd": 20181213,
         "trdPrc": 2243.58,
         "cmpprevddTpCd": "2",
         "opnprc": 2054.69,
         "hgprc": 2243.58,
         "lwprc": 2007.04,
         "accTrdvol": 250,
         "accTrdval": 6351,
         "cmpprevddPrc": 161.01 
      },

      {
         "BzDd": 20181212,
         "trdPrc": 2052.64,
         "cmpprevddTpCd": "5",
         "opnprc": 2132.14,
         "hgprc": 2229.67,
         "lwprc": 1984.03,
         "accTrdvol": 874,
         "accTrdval": 29458,
         "cmpprevddPrc": -0.33 
      },

      {
         "BzDd": 20181211,
         "trdPrc": 2134.77,
         "cmpprevddTpCd": "2",
         "opnprc": 2076.28,
         "hgprc": 2134.92,
         "lwprc": 2012.37,
         "accTrdvol": 764,
         "accTrdval": 31708,
         "cmpprevddPrc": 80.98 
      },

      {
         "BzDd": 20181210,
         "trdPrc": 2027.49,
         "cmpprevddTpCd": "5",
         "opnprc": 2048.45,
         "hgprc": 2061.78,
         "lwprc": 1845.79,
         "accTrdvol": 246,
         "accTrdval": 12553,
         "cmpprevddPrc": -48.27 
      },

      {
         "BzDd": 20181207,
         "trdPrc": 1705.57,
         "cmpprevddTpCd": "5",
         "opnprc": 2081.68,
         "hgprc": 2086.84,
         "lwprc": 1704.32,
         "accTrdvol": 1762,
         "accTrdval": 57237,
         "cmpprevddPrc": -363.12 
      },

      {
         "BzDd": 20181206,
         "trdPrc": 2068.69,
         "cmpprevddTpCd": "5",
         "opnprc": 2094.62,
         "hgprc": 2094.62,
         "lwprc": 2064,
         "accTrdvol": 537409,
         "accTrdval": 5606457,
         "cmpprevddPrc": -32.62 
      },

      {
         "BzDd": 20181205,
         "trdPrc": 2101.31,
         "cmpprevddTpCd": "5",
         "opnprc": 2086.57,
         "hgprc": 2107.69,
         "lwprc": 2086.57,
         "accTrdvol": 492716,
         "accTrdval": 4802792,
         "cmpprevddPrc": -13.04 
      },

      {
         "BzDd": 20181204,
         "trdPrc": 2114.35,
         "cmpprevddTpCd": "5",
         "opnprc": 2125.67,
         "hgprc": 2128.94,
         "lwprc": 2105.45,
         "accTrdvol": 507517,
         "accTrdval": 5539552,
         "cmpprevddPrc": -17.58 
      },

      {
         "BzDd": 20181203,
         "trdPrc": 2131.93,
         "cmpprevddTpCd": "2",
         "opnprc": 2127.78,
         "hgprc": 2136.64,
         "lwprc": 2113.6,
         "accTrdvol": 436588,
         "accTrdval": 5571246,
         "cmpprevddPrc": 35.07 
      },

      {
         "BzDd": 20181130,
         "trdPrc": 2096.86,
         "cmpprevddTpCd": "5",
         "opnprc": 2116.83,
         "hgprc": 2122.33,
         "lwprc": 2093.83,
         "accTrdvol": 427354,
         "accTrdval": 7316750,
         "cmpprevddPrc": -17.24 
      } 
    ] 
  } 
}
```
