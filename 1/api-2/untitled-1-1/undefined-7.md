# 주식 시세표

개별 종목기준 현재가 조회 대비 조회 빈도를 줄일수 있는 방식의 조회로 시장기준/복수종목기준 방식을 제공 

## Syntax

HTTP methods   \|   **GET**

Authentication    \|   **API Key**

{% hint style="danger" %}
별도의 시세표 **라이센스 필요**
{% endhint %}





## 현재가 시세표 API

시장기준으로 1회 조회 요청 시 전종목의 현재가\(1초주기\)를 리스트 형식으로 제공

현재가      \|   현재가, 누적거래량, 누적거래대금  
제공시장  \|   유가증권, 코스닥시장

{% api-method method="get" host="https://{APIGWAddr}" path="/v2/market/multiquote/stocks/{marketcode}/pricelist" %}
{% api-method-summary %}
/v2/market/multiquote/stocks/{marketcode}/pricelist
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분\(kospi \| kosdaq\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "trdDd": "20180508",
   "trdTm": "134447",
   "isuLists": [ 
    {
       "isuSrtCd": "000020",
       "trdPrc": 11250,
       "accTrdvol": 55286,
       "accTrdval": 625032300 
    },
    {
       "isuSrtCd": "000030",
       "trdPrc": 15450,
       "accTrdvol": 769087,
       "accTrdval": 11899058650 
    },
       ...이하 생략...
    ]
 }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





## 시고저종 시세표 API

시장기준으로 1회 조회 요청 시 시고저종을  리스트 형식으로 제공

시고저종  \|  시가, 고가, 저가, 종가\(현재가\)  
제공시장  \|  유가증권, 코스닥시장

{% api-method method="get" host="https://{APIGWAddr}" path="/v2/market/multiquote/stocks/{marketcode}/ohlclists" %}
{% api-method-summary %}
/v2/market/multiquote/stocks/{marketcode}/ohlclists
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" required=true name="marketcode" %}
시장구분\(kospi \| kosdaq\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "trdDd": "20180508",
   "trdTm": "134932",
   "isuLists": [ 
    {
       "isuSrtCd": "000020",
       "opnprc": 11550,
       "hgprc": 11550,
       "lwprc": 11200,
       "trdPrc": 11200 
    },
     
    {
       "isuSrtCd": "000030",
       "opnprc": 15350,
       "hgprc": 15600,
       "lwprc": 15350,
       "trdPrc": 15450 
    },
    ...이하 생략...
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





## 복수종목 현재가 시세표 API

**현재가** 실시간조회를 최대 20개의 임의의 종목에 대해 일괄적으로 조회  
복수종목 리스트간 구분자는 쉼표\(,\) 임

제공시장  \|  유가증권 , 코스닥 시장

{% api-method method="get" host="https://{APIGWAddr}" path="/v2/market/multiquote/stocks/{marketcode}/price" %}
{% api-method-summary %}
/v2/market/multiquote/stocks/{marketcode}/price
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분\(kospi \| kosdaq\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter type="string" name="isuCd" required=true %}
종목코드 ex\) 005930,000660
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
     "isulist": [ 
      {
         "trdPrc": 52700,
         "cmpprevddTpCd": "2",
         "opnprc": 52600,
         "hgprc": 53200,
         "lwprc": 51900,
         "accTrdvol": 17128652,
         "trdTm": 13352600,
         "trdvol": 100,
         "accTrdval": 904326766200,
         "cmpprevddPrc": 800,
         "isuSrtCd": "005930",
         "bidordPrc_1": 52700,
         "askordPrc_1": 52800,
         "lstAskbidTpCd": 1 
      },
       
      {
         "trdPrc": 84200,
         "cmpprevddTpCd": "2",
         "opnprc": 84500,
         "hgprc": 85300,
         "lwprc": 84200,
         "accTrdvol": 2127450,
         "trdTm": 13352800,
         "trdvol": 6,
         "accTrdval": 180271767300,
         "cmpprevddPrc": 1200,
         "isuSrtCd": "000660",
         "bidordPrc_1": 84200,
         "askordPrc_1": 84300,
         "lstAskbidTpCd": 1 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





## 복수종목  호가잔량 시세표 API

**호가잔량** 실시간조회를 최대 20개의 임의의 종목에 대해 일괄적으로 조회  
복수종목 리스트간 구분자는 쉼표\(,\) 임

제공시장  \|  유가증권 , 코스닥 시장

{% api-method method="get" host="https://{APIGWAddr}" path="/v2/market/multiquote/stocks/{marketcode}/orderbook" %}
{% api-method-summary %}
/v2/market/list/{marketcode}/orderbook
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter type="string" name="marketcode" required=true %}
시장구분\(kospi \| kosdaq\)
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter type="string" name="isuCd" required=true %}
종목코드 ex\) 005930,000660
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
     "isulist": [ 
      {
         "askStep1BstordPrc": 52900,
         "askStep2BstordPrc": 53000,
         "askStep3BstordPrc": 53100,
         "askStep4BstordPrc": 53200,
         "askStep5BstordPrc": 53300,
         "askStep6BstordPrc": 53400,
         "askStep7BstordPrc": 53500,
         "askStep8BstordPrc": 53600,
         "askStep9BstordPrc": 53700,
         "askStep10BstordPrc": 53800,
         "askStep1BstordRqty": 139074,
         "askStep2BstordRqty": 281770,
         "askStep3BstordRqty": 212990,
         "askStep5BstordRqty": 184279,
         "askStep6BstordRqty": 193079,
         "askStep7BstordRqty": 345397,
         "askStep8BstordRqty": 105715,
         "askStep9BstordRqty": 120527,
         "askStep10BstordRqty": 185815,
         "bidStep1BstordPrc": 52800,
         "bidStep2BstordPrc": 52700,
         "bidStep3BstordPrc": 52600,
         "bidStep4BstordPrc": 52500,
         "bidStep5BstordPrc": 52400,
         "bidStep6BstordPrc": 52300,
         "bidStep7BstordPrc": 52200,
         "bidStep8BstordPrc": 52100,
         "bidStep9BstordPrc": 52000,
         "bidStep10BstordPrc": 51900,
         "bidStep1BstordRqty": 62413,
         "bidStep2BstordRqty": 111228,
         "bidStep3BstordRqty": 146574,
         "bidStep4BstordRqty": 218182,
         "bidStep5BstordRqty": 62703,
         "bidStep6BstordRqty": 66254,
         "bidStep7BstordRqty": 62890,
         "bidStep8BstordRqty": 104846,
         "bidStep9BstordRqty": 262768,
         "bidStep10BstordRqty": 105522,
         "askordTotRqty": 2046762,
         "bidordTotRqty": 1203380,
         "pstoffhrAskTotOrdRqty": 0,
         "pstoffhrBidTotOrdRqty": 0,
         "accTrdvol": 17218791,
         "deemTrdPrc": 52600,
         "deemTrdvol": 439,
         "deemAccTrdvol": 2122875,
         "isuSrtCd": "005930" 
      },
       
      {
         "askStep1BstordPrc": 84300,
         "askStep2BstordPrc": 84400,
         "askStep3BstordPrc": 84500,
         "askStep4BstordPrc": 84600,
         "askStep5BstordPrc": 84700,
         "askStep6BstordPrc": 84800,
         "askStep7BstordPrc": 84900,
         "askStep8BstordPrc": 85000,
         "askStep9BstordPrc": 85100,
         "askStep10BstordPrc": 85200,
         "askStep1BstordRqty": 931,
         "askStep2BstordRqty": 7927,
         "askStep3BstordRqty": 10981,
         "askStep5BstordRqty": 16667,
         "askStep6BstordRqty": 18654,
         "askStep7BstordRqty": 18917,
         "askStep8BstordRqty": 49922,
         "askStep9BstordRqty": 21772,
         "askStep10BstordRqty": 31247,
         "bidStep1BstordPrc": 84200,
         "bidStep2BstordPrc": 84100,
         "bidStep3BstordPrc": 84000,
         "bidStep4BstordPrc": 83900,
         "bidStep5BstordPrc": 83800,
         "bidStep6BstordPrc": 83700,
         "bidStep7BstordPrc": 83600,
         "bidStep8BstordPrc": 83500,
         "bidStep9BstordPrc": 83400,
         "bidStep10BstordPrc": 83300,
         "bidStep1BstordRqty": 9106,
         "bidStep2BstordRqty": 10650,
         "bidStep3BstordRqty": 13948,
         "bidStep4BstordRqty": 5696,
         "bidStep5BstordRqty": 6064,
         "bidStep6BstordRqty": 4824,
         "bidStep7BstordRqty": 3514,
         "bidStep8BstordRqty": 9080,
         "bidStep9BstordRqty": 3684,
         "bidStep10BstordRqty": 11752,
         "askordTotRqty": 185835,
         "bidordTotRqty": 78318,
         "pstoffhrAskTotOrdRqty": 0,
         "pstoffhrBidTotOrdRqty": 0,
         "accTrdvol": 2141561,
         "deemTrdPrc": 84500,
         "deemTrdvol": 0,
         "deemAccTrdvol": 164843,
         "isuSrtCd": "000660" 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



