---
description: 금융투자회사(증권사) 제공
---

# 일임매매 서비스

일임주문 연계조회 API는 증권사별로 호출 URI가 다르나 큰 틀은 동일하며 단지 증권사구분이 URI에 포함되어 있는 구조입니다.

{% hint style="success" %}
일임매매 연계 API 는 [개발자센터-일임매매 연계 API](https://developers.koscom.co.kr/documentation/b2baccount) 에서 테스트할 수 있습니다.
{% endhint %}

{% hint style="danger" %}
제공대상 :  일임 투자자문이나 자산운용 회사 등의 금융기관 \(협의 필요\)
{% endhint %}



## Syntax

HTTP methods    \|   **POST**

Authentication     \|   **Basic Authentication**





## 주문체결 조회 API

계좌의 주문 체결 내역을 상세히 조회하기 위한 API

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/b2baccount" path="/orderdetail/search" %}
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

#### Request Parameters

| **Name** | **Type** | **Description** | ​ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 | ​ |
| srvId | string\(20\) | 핀테크 서비스 코드 | ​ |
| reqIdPlatform | string\(50\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| qrAssetType | String\(8\) | 자산유형 | EQTY\(주식\), FUND\(펀드\), ETC\(기타\) |
| qrSellBuyType | String\(8\) | 매도수구분 | 0\(전체\), 1\(매도\), 2\(매수\) |
| qrAccNo | String\(20\) | 계좌번호 |  |
| qrOrderDate | String\(12\) | 주문일자 | 선택 / \(입력없는경우 당일YYYYMMDD\) |
| qrIsinCode | String\(20\) | 종목코드 | 선택 / \(입력 시 해당 종목만 요청\) |
| qrOrderNo | String\(20\) | 주문번호 | 선택 / \(입력 시 해당 주문만 조회\) |
| count | number | 응답별 최대 응답 건수 | 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 |
| page | **String\(100\)** | 다음page를 지시하는 키 | 선택 / 첫 요청은 null로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청함 |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(50\) | 플랫폼에서 사용하는 메시지 구분자 |  |
| reqIdConsumer | String\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | . | 사용안함 |
| ci | String\(88\) | 연계정보 | 사용안함 |
| totalCnt	 | Number | 총 메시지 건수 |  |
| count	 | Number | 메시지 내 응답 건수 |  |
| page	 | String\(100\) | 다음 page 번호 | null이면 더 이상 없음 |
| accNo | String\(20\) | 계좌번호 |  |
| accName | String\(20\) | 계좌명 |  |
| modifyType | String\(8\) | 정정구분 | 0\(정상\), 1\(정정\) |
| cancelType | String\(8\) | 취소구분 | 0\(정상\), 1\(취소\) |
| orderNo | String\(20\) | 주문번호 |  |
| orgOrderNo | String\(20\) | 원주문번호 |  |
| sellBuyType | String\(8\) | 매도수구분 | 1\(매도\), 2\(매수\) |
| orderType | String\(20\) | 주문유형 | Text표기 |
| exchange | String\(8\) | KRX를 제외한 시장의 거래소명 | Text표기 |
| crcyCode | String\(20\) | 외화의 경우 통화코드 표기 |  |
| orderQty | Number | 주문수량 |  |
| orderPrice | Number | 주문단가 |  |
| execSumQty | Number | 체결합계수량 |  |
| orderExecType | String\(20\) | 주문체결구분 | 접수전, 정정, 취소확인, 거부 등 |
| cmsnType | String\(20\) | 수수료유형 | Text표기 |
| settDays | Number | 결제일수 |  |
| buyQtyUnit | Number | 매수수량단위 |  |
| sellQtyUnit | Number | 매도수량단위 |  |
| orderTime | String\(12\) | 주문시각 |  |
| orderRejectReason | String\(20\) | 주문거부사유 | Text표기 |
| isinType | String\(20\) | 종목코드종류 | 표준코드,축약코드, 축약영문 등 |
| isinCode | String\(20\) | 종목코드 |  |
| isinName | String\(40\) | 종목명 |  |
| execQty | Number | 체결 수량 |  |
| execPrice | Number | 체결 단가 |  |
| execNo | Number | 체결번호 |  |
| execTime | String\(12\) | 체결시각 |  |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |





## 일임 계좌잔고 조회 API

조회대상이 되는 계좌의 실제 잔고 수량, 평가손익 등을 상세히 조회하기 위한 API  
오전 08:30이전과 오후 16:00 이후 조회 가능

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/b2baccount" path="/balancelist/search" %}
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

#### Request Parameters {#request-parameters}

| **Name** | **Type** | **Description** | ​ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 | ​ |
| srvId | string\(20\) | 핀테크 서비스 코드 | ​ |
| reqIdPlatform | string | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | ​ |
| qrAssetType | String\(8\) | 자산유형 | EQTY\(주식\), FUND\(펀드\), ETC\(기타\) |
| qrAccNo | String\(20\) | 계좌번호 | ​ |
| count | number | 응답별 최대 응답 건수 | ​ |
| page | **String\(100\)** | 다음page를 지시하는 키 | ​ |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(50\) | 플랫폼에서 사용하는 메시지 구분자 |  |
| reqIdConsumer | String\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | . | 사용안함 |
| ci | String\(88\) | 연계정보 | 사용안함 |
| totalCnt	 | Number | 총 메시지 건수 |  |
| count	 | Number | 메시지 내 응답 건수 |  |
| page	 | String\(100\) | 다음 page 번호 | null이면 더 이상 없음 |
| accNo | String\(20\) | 계좌번호 |  |
| accName | String\(20\) | 계좌명 |  |
| cashBalance | Number | 현금잔고 |  |
| margin | Number | 증거금 |  |
| substitute | Number | 대용금 |  |
| receivable | Number | 미수미납금 |  |
| totCreditAmt | Number | 총대출금 |  |
| totlLoanAmt | Number | 총신용금액 |  |
| valAtCur | Number | 평가금액 |  |
| crcyCode | String\(8\) | 통화코드 | 국제 통화코드 표기 |
| cashAvWithdraw | Number | 출금가능현금 |  |
| assetType | String\(8\) | 자산유형 | 상품유형 표 참조 |
| exchange | String\(20\) | KRX를 제외한 시장의 거래소명 | 대표적으로 해외주식 |
| crcyCode | String\(8\) | 외화의 경우 통화코드 표기 |  |
| loanCreditType | String\(20\) | 신용/대출구분 | Text표기 |
| loanCreditAmt | Number | 신용/대출금 |  |
| qty | Number | 잔고수량 |  |
| valAtTrade | Number | 매수금액 |  |
| valAtCur | Number | 평가금액 |  |
| proLoss | Number | 평가손익 |  |
| earningRate | Number | 수익률 | 소수점 2째자리까지 |
| lastBuyDate | String\(12\) | 최종매수일 | YYYYMMDD |
| maturity | String\(12\) | 만기일 | YYYYMMDD |
| foreignDeposit | Number | 외화예수금 |  |
| wonDeposit | Number | 원화예수금 |  |
| currencyRate | Number | 기준환율 |  |
| isinType | String\(20\) | 종목코드종류 | 표준코드,축약코드, 축약영문 등 |
| isinCode | String\(20\) | 종목코드, 펀드코드, 상품코드 |  |
| isinName | String\(40\) | 종목명, 펀드명, 상품코드명 |  |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |







## 결제예정 정산 조회 API

전일 및 당일 주문 체결 내역에 대한 매매정리 내역을 상세히 조회하기 위한 API  
오전 08:30이전과 오후 16:00 이후 조회 가능

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/b2baccount" path="/settlelist/search" %}
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

####  Request Parameters

| **Name** | **Type** | **Description** | ​ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 | ​ |
| srvId | string\(20\) | 핀테크 서비스 코드 | ​ |
| reqIdPlatform | string\(50\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | ​ |
| qrAssetType | String\(8\) | 자산유형 | EQTY\(주식\), FUND\(펀드\), ETC\(기타\) |
| qrSellBuyType | String\(8\) | 매도수구분 | 0\(전체\), 1\(매도\), 2\(매수\) |
| qrAccNo | String\(20\) | 계좌번호 | ​ |
| qrOrderDate | String\(12\) | 주문일자 | 결제 전인 경우만 입력, 입력없음 당일\(YYYYMMDD\) |
| qrIsinCode | String\(20\) | 종목코드 | 입력 시 해당 종목만 요청 |
| count | number | 응답별 최대 응답 건수 | ​증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 |
| page | **String\(100\)** | 다음page를 지시하는 키 | ​첫 요청은 null\(“null”\)로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청함 |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(50\) | 플랫폼에서 사용하는 메시지 구분자 |  |
| reqIdConsumer | String\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 | 사용안함 |
| totalCnt	 | Number | 총 메시지 건수 |  |
| count	 | Number | 메시지 내 응답 건수 |  |
| page	 | String\(100\) | 다음 page 번호 | null이면 더 이상 없음 |
| accNo | String\(20\) | 계좌번호 |  |
| accName | String\(20\) | 계좌명 |  |
| sellBuyType | String\(8\) | 매도수구분 | 1\(매도\), 2\(매수\) |
| exchange | String\(8\) | KRX를 제외한 시장의 거래소명 | Text표기 |
| crcyCode | String\(20\) | 외화의 경우 통화코드 표기 |  |
| settQty | Number | 결제수량 |  |
| settAmt | Number | 결제금액 |  |
| tradeType | String\(20\) | 거래유형 | Text 표기 |
| loanCreditDate | String\(12\) | 신용/대출일 | YYYYMMDD |
| loanCreditAmt | Number | 신용/대출금액 |  |
| settDate | String\(12\) | 결제일자 |  |
| costTotal | Number | 비용합계 |  |
| isinType | String\(20\) | 종목코드종류 | 표준코드, 펀드코드, 단축코드, 상품코드 등 |
| isinCode | String\(20\) | 종목코드, 펀드코드, 상품코드 |  |
| isinName | String\(40\) | 종목명, 펀드명, 상품코드명 |  |
| costName | String\(20\) | 비용명 | 수수료, 거래세, 농특세, 주민세 등 |
| cost | Number | 비용금액 |  |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |







## 일임설정 계좌 조회 API

핀테크 기업의 일임 설정 계좌의 정보 조회하기 위한 API

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/b2baccount" path="/accountlist/search" %}
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

#### Request Parameters

| **Name** | **Type** | **Description** | ​ |
| --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 | ​ |
| srvId | string\(20\) | 핀테크 서비스 코드 | ​ |
| reqIdPlatform | string\(50\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 | ​ |
| count | number | 응답별 최대 응답 건수 | ​증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 |
| page | **String\(100\)** | 다음page를 지시하는 키 | ​첫 요청은 null\(“null”\)로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청함 |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(50\) | 플랫폼에서 사용하는 메시지 구분자 |  |
| reqIdConsumer | String\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 | 사용안함 |
| totalCnt | Number | 총 메시지 건수 |  |
| count	 | Number | 메시지 내 응답 건수 |  |
| page	 | String\(100\) | 다음 page 번호 | null이면 더 이상 없음 |
| accNo | String\(20\) | 계좌번호 |  |
| accName | String\(20\) | 계좌명 |  |
| virtualAccNo | String\(20\) | 가상계좌번호 |  |
| contractStatus | String\(8\) | 일임설정상태 | 0\(계약\), 1\(해지\), 2\(만기\) |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |





## 일임계좌 거래내역 조회 API

계좌의 거래내역을 상세히 조회하기 위한 API

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/b2baccount" path="/tradebook/search" %}
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

####  Request Parameters

| **Name** | **Type** | **Description** | ​ |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 | ​ |
| srvId | string\(20\) | 핀테크 서비스 코드 | ​ |
| reqIdPlatform | string\(50\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 | ​ |
| qrAccNo | String\(20\) | 계좌번호 |  |
| qrFromDate | String\(12\) | 조회시작날짜 | YYYYMMDD |
| qrToDate | String\(12\) | 조회종료날짜 | YYYYMMDD |
| count | number | 응답별 최대 응답 건수 | ​증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 |
| page | **String\(100\)** | 다음page를 지시하는 키 | ​첫 요청은 null\(“null”\)로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청함 |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(50\) | 플랫폼에서 사용하는 메시지 구분자 |  |
| reqIdConsumer | String\(50\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 | 사용안함 |
| qrAccNo | String\(20\) | 계좌번호 |  |
| qrFromDate | String\(12\) | 조회시작날짜 | YYYYMMDD |
| qrToDate | String\(12\) | 조회종료날짜 | YYYYMMDD |
| count | Number | . |  |
| page | String\(100\) | . |  |
| totalCnt | Number | 총 메시지 건수 |  |
| count	 | Number | 메시지 내 응답 건수 |  |
| page	 | String\(100\) | 다음 page 번호 | null이면 더 이상 없음 |
| tradeBook | Array | 거래 |  |
| accNo | String\(20\) | 계좌번호 |  |
| accName | String\(20\) | 계좌명 |  |
| transDate | String\(12\) | 거래일자 | YYYYMMDD |
| transType | String\(8\) | 거래구분 | BID\(매도\), ASK\(매수\),DEP\(이체입금\), WID\(이체출금\) |
| changeAmt | Number | 금액증감 | 매도/매수/이체에 따른 금액변동으로 감소 시 “-“ 표기 |
| changeQty | Number | 수량증감 | 매도/매수/출고에 따른 변동으로 수량 감소 시 “-“ 표기 |
| qty | Number | 잔고수량 | 거래 후 잔량 |
| amt | Number | 예수금 | 거래 후 현금 |
| exchange | String\(20\) | 거래소명 | Text표기 |
| crcyCode | String\(8\) | 통화코드 |  |
| subject | String\(40\) | 계정명 | Text표기 |
| summary | String\(40\) | 적요명 | Text표기 |
| isinType | String\(20\) | 종목코드 종류 | Text 표기 |
| isinCode | String\(20\) | 종목코드, 펀드코드, 상품코드 등 |  |
| isinName | String\(40\) | 종목명 |  |
| costName | String\(20\) | 비용명 | Text 표기 |
| cost | Number | 비용 |  |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |



