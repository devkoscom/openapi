# format sample \(GET\)

KOSPI/KOSDAQ등의 지수 예상지수 및 업종별 투자자별 거래량등을 제공한다.



## Syntax

HTTP methods    \|   **GET**

Authentication     \|   **API Key**



{% hint style="info" %}
업종지수 스트리밍 조회는 xx를 참고하세요.
{% endhint %}

{% hint style="warning" %}
`marketcode` 및 `issuecode` 는 [코드표 &gt; "시장코드표"](https://koscom.gitbook.io/open-api/untitled-1/undefined-8#undefined)를 참조하세요.
{% endhint %}







## 상품/지수선물 종가

{% api-method method="get" host="https://{APIGWAddr}/v2/market/futures" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/closeprice
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
ddddd
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | String\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 |  |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |





## 상품/지수선물 체결

{% api-method method="get" host="https://{APIGWAddr}/v2/market/futures" path="/{marketcode}/{issuecode}/price" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/price
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter name="issuecode" type="string" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": [ " -" 
    ],
     "trdPrc": null,
     "opnprc": null,
     "hgprc": null,
     "lwprc": null,
     "accTrdvol": null,
     "trdTm": null,
     "trdvol": null,
     "lstTrdTpCd": 0,
     "accTrdval": null,
     "fstmmAgndaContrtPrc": null,
     "futrmmAgndaContrtPrc": null,
     "negoBlkAccTrdvol": null,
     "realtmUplmtprc": null,
     "realtmLwlmtprc": null 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | string\(12\) | 종목단축코드 | 표준코드 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 |  |
| trdvol | number\(10\) | 체결수량, 거래량 | 단위:주 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 일반체결수량+협의대량체결수량+EFP누적체결수량 /2009.08.31 |
| accTrdval | number\(22\) | 누적거래대금 | 일반체결대금+협의대량체결대금+EFP누적체결대금 /2009.08.31 |
| negoBlkAccTrdvol | number\(12\) | 협의대량누적체결수량 |  |
| lstAskbidTpCd | string\(1\) | 최종매도매수구분코드 | 1:매도, 2:매수 \(최종으로 들어온 호가의 매도매수구분값\) |
| trdTm | string\(8\) | 체결시각,거래시각 |  |
| fstmmAgndaContrtPrc | number\(11\) | 최근월물의제약정가격 |  |
| futrmmAgndaContrtPrc | number\(11\) | 원월물의제약정가격 |  |
| realtmUplmtprc | number\(11\) | 실시간상한가 |  |
| realtmLwlmtprc | number\(11\) | 실시간하한가 |  |





## 상품/지수선물 종목 체결

{% api-method method="get" host="https://{APIGWAddr}/v2/market/futures" path="/{marketcode}/{issuecode}/price" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/price
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}

{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "jsonrpc": "2.0",
   "result": 
  {
     "isuSrtCd": [ " -" 
    ],
     "trdPrc": null,
     "opnprc": null,
     "hgprc": null,
     "lwprc": null,
     "accTrdvol": null,
     "trdTm": null,
     "trdvol": null,
     "lstTrdTpCd": 0,
     "accTrdval": null,
     "fstmmAgndaContrtPrc": null,
     "futrmmAgndaContrtPrc": null,
     "negoBlkAccTrdvol": null,
     "realtmUplmtprc": null,
     "realtmLwlmtprc": null 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | string\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 | 0 |
| trdvol | number\(10\) | 체결수량, 거래량 | 단위:주 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 일반체결수량+협의대량체결수량+EFP누적체결수량 2009.08.31 |
| accTrdval | number\(22\) | 누적거래대금 | 일반체결대금+협의대량체결대금+EFP누적체결대금 2009.08.31 |
| negoBlkAccTrdvol | number\(12\) | 협의대량누적체결수량 |  |
| lstAskbidTpCd | string\(1\) | 최종매도매수구분코드 | 1:매도, 2:매수 \(최종으로 들어온 호가의 매도매수구분값\) |
| trdTm | string\(8\) | 체결시각,거래시각 |  |
| fstmmAgndaContrtPrc | number\(11\) | 최근월물의제약정가격 |  |
| futrmmAgndaContrtPrc | number\(11\) | 원월물의제약정가격 |  |
| realtmUplmtprc | number\(11\) | 실시간상한가 |  |
| realtmLwlmtprc | number\(11\) | 실시간하한가 |  |

> `secugrpId`   
> ST:주권, MF:증권투자회사, RT:부동산투자회사, SC:선박투자회사, IF:사회간접자본투융자회사, DR:주식예탁증서, EW:ELW, EF:ETF, SW:신주인수권증권, SR:신주인수권증서, BC:수익증권, FE:해외ETF, FS:외국주권, EN:ETN 
>
> `mktWarnTpCd`  
> 00:해당없음\(시장경보가 지정될 수 있는 종목에 대해서 지정된바가 없음을 의미\),   
> 01:투자주의, 02:투자경고, 03:투자위험



