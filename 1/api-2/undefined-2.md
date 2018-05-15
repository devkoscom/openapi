# 일임매매서비스

일임주문 연계조회 API는 증권사별로 호출 URI가 다르나 큰 틀은 동일하며 단지 증권사구분이 URI에 포함되어 있는 구조입니다. API는 버전으로 구분되기 때문에 URI에 버전정보가 포함되어 있습니다. 

{% hint style="success" %}
일임매매 연계 API는 [개발자센터-일임매매 연계 API](https://developers.koscom.co.kr/documentation/b2baccount)에서 이용할 수 있습니다:
{% endhint %}



#### Syntax

* HTTP methods
  * **POST**
* Authentication
  * **Basic Authentication**



### 조회 유의사항

조회는 API에 지정된 가상계좌를 조회범위로 하기 때문에 계좌속성\(위탁, 펀드, 파생상품 등\)에 따라 조회조건이 충족되지 않을 수 있으므로 전 상품군을 대상으로 조회할 경우는 주의가 필요합니다. 예로 보통 증권회사의 종합계좌는 모든 금융상품을 취급할 수 있는 것이지만 경우에 따라 파생상품과 같은 특정 상품군은 별도로 관리되는 증권회사도 있으며, 종합계좌 개념을 도입하지 않는 증권사도 존재합니다. 따라서 종합계좌라고 판단되어 KOSPI200 파생상품 잔고를 조회하였을 때 응답에 해당상품이 반드시 포함될 것이라 판단하고 비즈니스를 설계하면 안됩니다. 

예로 계좌잔고조회의 경우 모든 상품군을 조회범위에 포함하는 ‘ALL’검색조건을 지원하는 증권사의 경우 해당 조건으로 모든 계좌를 조회하면 문제가 없지만, ‘ALL’검색조건을 지원하지 않는 증권사의 경우 각 상품군별로 모든 계좌를 대상으로 조회해야 누락 없이 전 상품군을 조회할 수 있습니다.





## 주문체결 조회 API

계좌의 주문 체결 내역을 상세히 조회하기 위한 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/b2baccount" path="/orderdetail/search" %}
{% api-method-summary %}
/b2baccount/orderdetail/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" required=true type="string" %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter name="comId" required=true type="string" %}
오픈 플랫폼으로부터 발급받은 기관 코드번호
{% endapi-method-parameter %}

{% api-method-parameter name="authorization" required=true type="string" %}
Basic Authentication 인증 사용
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "commonHeader": 
  {
     "reqIdPlatform": "5b19a7a5-443a-4b6b-a22b-17a627d3561b",
     "reqIdConsumer": "Fintech-2016062200001",
     "certDn": null,
     "ci": null 
  },
   "resp": 
  {
     "respCode": "200",
     "respMsg": "OK" 
  },
   "orderDetailListResponseBody": 
  {
     "queryParameter": 
    {
       "qrAssetType": "EQTY",
       "qrSellBuyType": "1",
       "qrAccNo": "001-01-992323232",
       "qrOrderDate": "20160622",
       "qrIsinCode": null,
       "qrOrderNo": null,
       "count": 0,
       "page": null 
    },
     "queryResult": 
    {
       "totalCnt": 0,
       "count": 0,
       "page": null 
    } 
  },
   "orderDetailList": 
  {
     "orderDetail": [ 
      {
         "accNo": "001-01-992323232",
         "accName": "일임계좌",
         "modifyType": "0",
         "cancelType": "0",
         "orderNo": null,
         "orgOrderNo": null,
         "sellBuyType": "1",
         "orderType": null,
         "exchange": null,
         "crcyCode": null,
         "orderQty": 0,
         "orderPrice": 0,
         "execSumQty": 0,
         "orderExecType": null,
         "cmsnType": null,
         "settDays": 0,
         "buyQtyUnit": 0,
         "sellQtyUnit": 0,
         "orderTime": "2016062211262636",
         "orderRejectReason": null,
         "isinInfo": [ 
          {
             "isinType": null,
             "isinCode": "KR7000020008",
             "isinName": "동화약품" 
          } 
        ],
         "execList": [ 
          {
             "execQty": 0,
             "execPrice": 0,
             "execNo": 0,
             "execTime": null 
          } 
        ] 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example {#example}

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
    "partner": {
        "comId": "F9999",
        "srvId": "999"
    },
    "commonHeader": {
        "reqIdConsumer": "Fintech-2016062200001"
    },
    "orderDetailListRequestBody": {
        "queryParameter": {
            "qrAssetType": "EQTY",
            "qrSellBuyType": "1",
            "qrAccNo": "0019923122221",
            "qrOrderDate": "20160622",
            "qrIsinCode": null,
            "qrOrderNo": null,
            "count": 0,
            "page": null
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}







## 일임 계좌잔고 조회 API

 조회대상이 되는 계좌의 실제 잔고 수량, 평가손익 등을 상세히 조회하기 위한 API로 오전 08:30이전과 오후 16:00 이후 조회 가능

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/b2baccount" path="/balancelist/search" %}
{% api-method-summary %}
/b2baccount/balancelist/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter name="comId" type="string" required=true %}
오픈 플랫폼으로부터 발급받은 기관 코드번호
{% endapi-method-parameter %}

{% api-method-parameter name="authorization" type="string" required=true %}
Basic Authentication 인증 사용
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "commonHeader": 
  {
     "reqIdPlatform": "4e4fe6b0-5598-4bfb-8fbd-b1da17b411fa",
     "reqIdConsumer": "Fintech-2016062200001",
     "certDn": null,
     "ci": null 
  },
   "resp": 
  {
     "respCode": "200",
     "respMsg": "OK" 
  },
   "balanceListResponseBody": 
  {
     "queryParameter": 
    {
       "qrAssetType": "EQTY",
       "qrAccNo": "0019923122221",
       "count": 0,
       "page": "null" 
    },
     "queryResult": 
    {
       "totalCnt": 2,
       "count": 0,
       "page": "null" 
    } 
  },
   "balanceList": 
  {
     "balance": [ 
      {
         "accInfo": 
        {
           "accNo": "0019923122221",
           "accName": "홍길동" 
        },
         "cashBalInfo": [ 
          {
             "cashBalance": 3000000,
             "margin": 2500000,
             "substitute": 5000000,
             "receivable": 0,
             "totCreditAmt": 0,
             "totLoanAmt": 3600000,
             "valAtCur": 5500000,
             "crcyCode": null,
             "cashAvWithdraw": 500000 
          } 
        ],
         "securitiesBalInfo": [ 
          {
             "assetType": "KSP",
             "exchange": null,
             "crcyCode": null,
             "loanCreditType": "자기융자",
             "loanCreditAmt": 3600000,
             "qty": 300,
             "valAtTrade": 9000000,
             "valAtCur": 8700000,
             "proLoss": -300000,
             "earningRate": -0.1,
             "lastBuyDate": "20170621",
             "maturity": "20170921",
             "foreignDeposit": 0,
             "wonDeposit": 0,
             "currencyRate": 0,
             "isinInfo": [ 
              {
                 "isinType": "표준코드",
                 "isinCode": "KR0065300",
                 "isinName": "삼성생명" 
              },
              {
                 "isinType": "단축코드",
                 "isinCode": "A06530",
                 "isinName": "삼성생명" 
              } 
            ] 
          },
          {
             "assetType": "KSP",
             "exchange": null,
             "crcyCode": null,
             "loanCreditType": null,
             "loanCreditAmt": 0,
             "qty": 120,
             "valAtTrade": 4000000,
             "valAtCur": 4400000,
             "proLoss": 400000,
             "earningRate": 0.1,
             "lastBuyDate": "20170621",
             "maturity": null,
             "foreignDeposit": 0,
             "wonDeposit": 0,
             "currencyRate": 0,
             "isinInfo": [ 
              {
                 "isinType": "표준코드",
                 "isinCode": "KR005930",
                 "isinName": "삼성전자" 
              },
              {
                 "isinType": "단축코드",
                 "isinCode": "A05930",
                 "isinName": "삼성전자" 
              } 
            ] 
          } 
        ] 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example {#example}

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
    "partner": {
        "comId": "F9999",
        "srvId": "100"
    },
    "commonHeader": {
        "reqIdConsumer": "Fintech-2016062200001"
    },
    "balanceListRequestBody": {
        "queryParameter": {
            "qrAccNo": "0019923122221",
            "qrAssetType": "EQTY",
            "count": 0,
            "page": null
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 



## 결제예정 정산 조회 API

전일 및 당일 주문 체결 내역에 대한 매매정리 내역을 상세히 조회하기 위한 API로 오전 08:30이전과 오후 16:00 이후 조회 가능

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/b2baccount" path="/settlelist/search" %}
{% api-method-summary %}
/b2baccount/settlelist/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" required=true type="string" %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter name="comId" required=true type="string" %}
오픈 플랫폼으로부터 발급받은 기관 코드번호
{% endapi-method-parameter %}

{% api-method-parameter name="authorization" required=true type="string" %}
Basic Authentication 인증 사용
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "commonHeader": 
  {
     "reqIdPlatform": "702889e9-3477-40fd-9711-299c7f4e2b24",
     "reqIdConsumer": "Fintech-2016062200001",
     "certDn": null,
     "ci": null 
  },
   "resp": 
  {
     "respCode": "200",
     "respMsg": "OK" 
  },
   "settleListResponseBody": 
  {
     "queryParameter": 
    {
       "qrAssetType": "KSP",
       "qrSellBuyType": "0",
       "qrAccNo": "0019923122221",
       "qrOrderDate": "20170627",
       "qrIsinCode": "KR0065300",
       "count": 0,
       "page": "null" 
    },
     "queryResult": 
    {
       "totalCnt": 1,
       "count": 0,
       "page": "null" 
    } 
  },
   "settleList": 
  {
     "settleInfo": [ 
      {
         "accNo": "0019923122221",
         "accName": "이지선",
         "sellBuyType": "1",
         "exchange": null,
         "crcyCode": null,
         "settQty": 300,
         "settAmt": 9000000,
         "tradeType": "자기융자매도",
         "loanCreditDate": "20170627",
         "loanCreditAmt": 360000,
         "settDate": "20170627",
         "costTotal": 171990,
         "isinInfo": [ 
          {
             "isinType": "표준코드",
             "isinCode": "KR0065300",
             "isinName": "삼성생명" 
          },
          {
             "isinType": "단축코드",
             "isinCode": "A06530",
             "isinName": "삼성생명" 
          } 
        ],
         "costInfo": [ 
          {
             "costName": "거래세",
             "cost": 45000 
          },
          {
             "costName": "주민세",
             "cost": 126000 
          },
          {
             "costName": "일반수수료",
             "cost": 990 
          } 
        ] 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Example {#example}

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
    "partner": {
        "comId": "F9999",
        "srvId": "100"
    },
    "commonHeader": {
        "reqIdConsumer": "Fintech-2016062200001"
    },
    "settleListRequestBody": {
        "queryParameter": {
            "qrAssetType": "EQTY",
            "qrSellBuyType": "0",
            "qrAccNo": "0019923122221",
            "qrOrderDate": "20170622",
            "qrIsinCode": "KR0065300",
            "count": 0,
            "page": null
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 



## 일임설정 계좌 조회 API

핀테크 기업의 일임 설정 계좌의 정보 조회하기 위한 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/b2baccount" path="/accountlist/search" %}
{% api-method-summary %}
/b2baccount/accountlist/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter type="string" name="Content-Type" required=true %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="comId" required=true %}
오픈 플랫폼으로부터 발급받은 기관 코드번호
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="authorization" required=true %}
Basic Authentication 인증 사용
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "commonHeader": 
  {
     "reqIdPlatform": "cc36edbf-e70b-4297-8e61-faafb2225c63",
     "reqIdConsumer": "Fintech-2016062200001",
     "certDn": null,
     "ci": null 
  },
   "resp": 
  {
     "respCode": "200",
     "respMsg": "OK" 
  },
   "accountListResponseBody": 
  {
     "queryParameter": 
    {
       "count": 0,
       "page": "null" 
    },
     "queryResult": 
    {
       "totalCnt": 1,
       "count": 0,
       "page": "null" 
    } 
  },
   "accountList": 
  {
     "account": [ 
      {
         "accNo": "0019923122221",
         "accName": "홍길동",
         "virtualAccNo": "0929923212342",
         "contractStatus": "0" 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example {#example-1}

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
    "partner": {
        "comId": "00995",
        "srvId": "100"
    },
    "commonHeader": {
        "reqIdConsumer": "Fintech-2016062200001"
    },
    "accountListRequestBody": {
        "queryParameter": {
            "count": 0,
            "page": null
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}





## 일임계좌 거래내역 조회 API

계좌의 거래내역을 상세히 조회하기 위한 API

{% api-method method="post" host="" path="/tradebook/search" %}
{% api-method-summary %}
/b2baccount/tradebook/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" required=true type="string" %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter name="comId" required=true type="string" %}
오픈 플랫폼으로부터 발급받은 기관 코드번호
{% endapi-method-parameter %}

{% api-method-parameter name="authorization" required=true type="string" %}
Basic Authentication 인증 사용
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "commonHeader": 
  {
     "reqIdPlatform": "88ea978a-22ab-4b32-9607-89c4fffaf103",
     "reqIdConsumer": "Fintech-2016062200001",
     "certDn": null,
     "ci": null 
  },
   "resp": 
  {
     "respCode": "200",
     "respMsg": "OK" 
  },
   "tradeBookListResponseBody": 
  {
     "queryParameter": 
    {
       "qrAccNo": "0019923122221",
       "qrFromDate": "20170622",
       "qrToDate": "20170627",
       "count": 0,
       "page": "null" 
    },
     "queryResult": 
    {
       "totalCnt": 1,
       "count": 0,
       "page": "null" 
    } 
  },
   "tradeBookList": 
  {
     "tradeBook": [ 
      {
         "isinInfo": [ 
          {
             "isinType": "표준코드",
             "isinCode": "KR0065300",
             "isinName": "삼성생명" 
          },
          {

             "isinType": "단축코드",
             "isinCode": "A06530",
             "isinName": "삼성생명" 
          } 
        ],
         "costInfo": [ 
          {
             "costName": "거래세",
             "cost": 45000 
          },
          {
             "costName": "주민세",
             "cost": 126000 
          },
          {
             "costName": "일반수수료",
             "cost": 990 
          } 
        ],
         "accNo": "0019923122221",
         "accName": "홍길동",
         "transDate": "20170622",
         "transType": "BID",
         "changeAmt": -9000000,
         "changeQty": 300,
         "qty": 300,
         "amt": 3000000,
         "exchange": null,
         "crcyCode": null,
         "subject": "위탁자",
         "summary": "이체출금" 
      } 
    ] 
  } 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example {#example}

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{
    "partner": {
        "comId": "00995",
        "srvId": "100"
    },
    "commonHeader": {
        "reqIdConsumer": "Fintech-2016062200001"
    },
    "tradeBookListRequestBody": {
        "queryParameter": {
            "qrAccNo": "0019923122221",
            "qrFromDate": "20170622",
            "qrToDate": "20170627",
            "count": 0,
            "page": "null"
        }
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 

