# 선물 시세조회

URI 입력값

- marketcode :  ☞ 코드표1  '시장코드표' 참조

- issuecode :  예\) KR4101C90009 → K101C9000



\* 종목코드\(issuecode\)  추가 :  연결선물코드

    - 선물최근월물의  종목히스토리 조회를 위해  사용가능하며,  현재가 조회시 조회결과 종목코드는 현재 

       기준 시장에서 거래되는 종목의  단축종목코드로 결과를 보내줌

       ☞ 코드표1  '시장코드표' 참조



## 상품/지수선물 종목 리스트

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/lists" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/lists
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "trdDd": "20180307",
   "mktEndTm": "1550",
   "isuLists": [ 
    {
       "isuSrtCd": "105N3000",
       "isuCd": "KR4105N30003",
       "isuKorNm": "MINI KOSPI200 선물 1803",
       "isuKorAbbr": "MINI K200 선물 1803",
       "map_to": "105N3000*103" 
    },
     
    {
       "isuSrtCd": "M2FA001",
       "isuCd": "KR4105N30003",
       "isuKorNm": "MINI KOSPI200 선물 1803",
       "isuKorAbbr": "MINI K200 선물 1803",
       "map_to": "M2FA001" 
    },
     
    {
       "isuSrtCd": "105N4000",
       "isuCd": "KR4105N40002",
       "isuKorNm": "MINI KOSPI200 선물 1804",
       "isuKorAbbr": "MINI K200 선물 1804",
       "map_to": "105N4000*103" 
    },
     
    {
       "isuSrtCd": "105N5000",
       "isuCd": "KR4105N50001",
       "isuKorNm": "MINI KOSPI200 선물 1805",
       "isuKorAbbr": "MINI K200 선물 1805",
       "map_to": "105N5000*103" 
    },
     
    {
       "isuSrtCd": "105N6000",
       "isuCd": "KR4105N60000",
       "isuKorNm": "MINI KOSPI200 선물 1806",
       "isuKorAbbr": "MINI K200 선물 1806",
       "map_to": "105N6000*103" 
    },
     
    {
       "isuSrtCd": "105N7000",
       "isuCd": "KR4105N70009",
       "isuKorNm": "MINI KOSPI200 선물 1807",
       "isuKorAbbr": "MINI K200 선물 1807",
       "map_to": "105N7000*103" 
    },
     
    {
       "isuSrtCd": "105N8000",
       "isuCd": "KR4105N80008",
       "isuKorNm": "MINI KOSPI200 선물 1808",
       "isuKorAbbr": "MINI K200 선물 1808",
       "map_to": "105N8000*103" 
    },
     
    {
       "isuSrtCd": "405N3N4S",
       "isuCd": "KR4405N3N4S3",
       "isuKorNm": "MINI K200 스프레드 N3N4",
       "isuKorAbbr": "MINI K200 SP N3N4",
       "map_to": "405N3N4S*103" 
    },
     
    {
       "isuSrtCd": "405N3N5S",
       "isuCd": "KR4405N3N5S0",
       "isuKorNm": "MINI K200 스프레드 N3N5",
       "isuKorAbbr": "MINI K200 SP N3N5",
       "map_to": "405N3N5S*103" 
    },
     
    {
       "isuSrtCd": "405N3N6S",
       "isuCd": "KR4405N3N6S8",
       "isuKorNm": "MINI K200 스프레드 N3N6",
       "isuKorAbbr": "MINI K200 SP N3N6",
       "map_to": "405N3N6S*103" 
    },
     
    {
       "isuSrtCd": "405N3N7S",
       "isuCd": "KR4405N3N7S6",
       "isuKorNm": "MINI K200 스프레드 N3N7",
       "isuKorAbbr": "MINI K200 SP N3N7",
       "map_to": "405N3N7S*103" 
    },
     
    {
       "isuSrtCd": "405N3N8S",
       "isuCd": "KR4405N3N8S4",
       "isuKorNm": "MINI K200 스프레드 N3N8",
       "isuKorAbbr": "MINI K200 SP N3N8",
       "map_to": "405N3N8S*103" 
    } 
  ] 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



## 상품/지수선물 종목 마스터

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/futures" path="/{marketcode}/{issuecode}/master" %}
{% api-method-summary %}
 /v2/market/futures/{marketcode}/{issuecode}/master
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="issuecode" required=true %}
종목코드
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
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
     "midyyHgstprc": null,
     "midyyHgstprcDd": null,
     "midyyLwstprc": null,
     "midyyLwstprcDd": null,
     "inlistHgstprc": null,
     "inlistHgstprcDd": null,
     "inlistLwstprc": null,
     "inlistLwstprcDd": null,
     "prevddClsprc": null,
     "prevddOpnprc": null,
     "prevddHgprc": null,
     "prevddLwprc": null,
     "prevddAccTrdvol": null,
     "prevddAccTrdval": null,
     "prevddOpnintQty": null,
     "setlPrcTheoPrcDivrgRt": null,
     "BzDd": 20180504,
     "basPrc": null,
     "isuKorNm": " -",
     "isuKorAbbrv": " -",
     "isuCd": " -",
     "listDd": null,
     "remainDys": null,
     "cdInt": null,
     "lsttrdDd": null,
     "expDd": null,
     "ulyId": " -",
     "prcLmtStep1Uplmtprc": null,
     "prcLmtStep2Uplmtprc": null,
     "prcLmtStep3Uplmtprc": null,
     "prcLmtStep1Lwlmtprc": null,
     "prcLmtStep2Lwlmtprc": null,
     "prcLmtStep3Lwlmtprc": null,
     "opnintLmtQty": null,
     "setlmult": null,
     "setlTheoPrc": null,
     "basTheoPrc": null 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





