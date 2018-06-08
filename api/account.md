# 계좌 서비스

계좌기반 조회 API는 증권사별로 호출 URI가 다르나 큰 틀은 동일하며 단지 증권사구분이 URI에 포함되어 있는 구조입니다. 

{% hint style="success" %}
계좌기반 조회 API 는 [개발자센터-계좌조회API](https://developers.koscom.co.kr/documentation/account) 에서 테스트할 수 있습니다.
{% endhint %}





## Syntax

HTTP methods    \|   **POST**

Authentication     \|   **OAuth2**





## 자산 포트폴리오 조회 API

조회대상이 되는 계좌의 실제 잔고 수량, 투자금액 대신 금융투자 상품의 구성비만을 제공함으로써 개인금융정보의 노출부담을 최소화하면서도 투자자산을 기초로 자산통합관리, 자문, 정보제공 등을 받을 수 있도록 하기 위한 API

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/account" path="/portfolio/search" %}
{% api-method-summary %}
/account/portfolio/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" required=true type="string" %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" required=true type="string" %}
Bearer 발급받은 access token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
  "commonHeader":{
    "reqIdPlatform":"fs27abe2231",
    "reqIdConsumer":"ID000001",
    "certDn":"",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
},
"accInfo":{
    "realAccNo":"",
      "vtAccNo":"160678007213500001"
    },
  "portfolioResponseBody":{
"queryType":{
      "assetType":"ALL",
      "rspType":"RAT",
      "count":"0",
      "page":"null"
    },
    "queryResult":{
      "totalCnt":157.0,
      "count":157.0,
      "page":"null"
    }
},
  "resp":{
    "respCode":"200",
    "respMsg":"OK"
  },
  "portfolioList":{
    "portfolio":{
        "cash":{
          "amt":6976542.0
      },
        "equityList":[
          {
            "assetType":"KSP",
            "isinCode":"HK0000050325",
            "qty":0.0,
            "earningRate":-12.9
          },
          {
            "assetType":"KDQ",
            "isinCode":"HK0000054723",
            "qty":0.0,
            "earningRate":-19.72
          },
          {
            "assetType":"KSP",
            "isinCode":"KR7000020008",
            "qty":0.0,
            "earningRate":10.95
          },
          {
            "assetType":"KSP",
            "isinCode":"KR7000270009",
            "qty":1.0,
            "earningRate":-3.97
          },
          {
            "assetType":"KSP",
            "isinCode":"KR7000400002",
            "qty":0.0,
            "earningRate":-2.68
          }
        ],
        "fundList":[
          {
            "fundCode":"KRZ500395135",
            "fundName":"삼성중소형FOCUS증권자1호[주식]",
            "qty":46.0,
            "earningRate":-9.58,
            "maturity":"00000000"
          },
          {
            "fundCode":"KRZ500395136",
            "fundName":"삼성중소형FOCUS증권자1호[주식]",
            "qty":5.0,
            "earningRate":-12.52,
            "maturity":"00000000"
          },
          {
            "fundCode":"KRZ501130561",
            "fundName":"미래에셋고배당포커스증권자1호(",
            "qty":5.0,
            "earningRate":-6.32,
            "maturity":"00000000"
          }
        ],
        "etcList":[
          {
            "assetType":"BOND",
            "assetName":"국민주택1종11-07",
            "qty":2.0,
            "earningRate":22.73
          },
          {
            "assetType":"BOND",
            "assetName":"국고03000-2409(14-5)",
            "qty":2.0,
            "earningRate":7.68
          },
{
            "assetType":"BOND",
            "assetName":"광주지방채11",
            "qty":2.0,
            "earningRate":4.53
          },
          {
            "assetType":"DLS",
            "assetName":"우리투자증권(DLS)1120",
            "qty":14.0,
            "earningRate":2.61
          },
          {
            "assetType":"ELS",
            "assetName":"NH투자증권(ELB)759",
            "qty":5.0,
            "earningRate":2.5
          },
          {
            "assetType":"CP",
            "assetName":"루카스 20131227-89-6",
            "qty":0.0,
            "earningRate":0.86
          },
{
            "assetType":"CP",
            "assetName":"루카스 20131227-89-14",
            "qty":0.0,
            "earningRate":0.86
          },
          {
            "assetType":"CP",
            "assetName":"루카스 20131227-89-15",
            "qty":0.0,
            "earningRate":0.86
          }
        ]
}
}
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{ 
  "partner":{ 
    "comId":"F9999",
    "srvId":"999"
  },
  "commonHeader":{ 
    "reqIdPlatform":"",
    "reqIdConsumer":"ID000001",
    "ci":"S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "devInfo":{ 
    "ipAddr":"123451234500",
    "macAddr":"7054D27EE247"
  },
  "accInfo":{ 
      "vtAccNo":"160678007213500001"
  },
  "portfolioRequestBody":{ 
    "queryType":{ 
      "assetType":"ALL",
      "rspType":"RAT",
      "count":0,
      "page":"null"
    }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### **Request Parameters**

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | String\(5\) | 핀테크기업코드 |  |
| srvId | String\(20\) | 핀테크서비스코드 |  |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크기업에서 사용하는 메시지 |  |
| ci | String\(88\) | 연계정보 |  |
| ipAddr | String\(32\) | 사용자 단말 IP주소  | dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정 |
| macAddr | String\(50\) | 사용자 MAC 주소 | PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| assetType | String\(8\) | 요청하는 자산유형 | CASH\(현금\), EQTY\(주식\), FUND\(펀드\), ETC\(기타자산\), ALL\(전체\)인 경우는 page 처리없이 대용량 데이터 전송이 가능한 증권사만 가능 |
| rspType | String\(8\) | 응답 유형 | RAT\(잔고구성비율\)은 기본으로 제공하며, 증권사에 따라 QTY\(실제잔고수량\)도 가능하나 본 API의 목적상 사용을 권장하지 않음 |
| count | Number | 응답 별 최대 응답 건수 | 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 / assetType이 ‘ALL’인 경우는 page없이 일괄전송이므로 본 필드는 의미 없으므로 0으로 설정 |
| page | String\(24\) | 다음 page를 지시하는 키 | 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청 |

{% hint style="success" %}
 `assetType`을 'ALL'로 요청 가능한 증권사    
   : NH투자증권, 대신증권, 키움증권, 신한금융투자 
{% endhint %}

{% hint style="warning" %}
**보유비중 조회**는 현재 일부 증권사의 경우 값이 부정확한 경우가 있고, 비중대신 수량을 제공하는 경우도 있으므로 주의 필요함. 보유비중은 수익기여도 \(해당 자산군에서 해당종목이 차지하는 수익기여도\)로 산출한 경우가 대부분이며, 증권사별 산출 기준은 추후 게시예정
{% endhint %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) | "" | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| totalCnt | Number | 조회 조건의 총 메시지 건수 |  |
| count | Number | 현 메시지 내 응답 건수 |  |
| page | String\(24\) | 다음 page 번호 | “null”이면 더 이상 없음 |
| amt | Number | 전체 자산 중 현금잔고 또는 비중  |  |
| equityList: assetType | String\(8\) | 상품구분자 | KSP\(코스피\), KDQ\(코스닥\), ETF\(ETF\), FUT\(선물\), OPT\(옵션\), ELW\(ELW\), ETC\(기타\) |
| equityList :isinCode | String\(12\) | ISINCODE\(12\) |  |
| qty | Number | 수량 또는 비중 | equity 내 비중, 소수점 2째자리까지 / 신용 매수 분 포함하고 대출잔고는 반영안함 |
| earningRate | Number | 수익률 | 소수점 2째자리까지 |
| fundCode | String\(20\) | 펀드표준코드 |  |
| fundName | String\(15\) | 펀드명 | 최대 15자 |
| maturity | String\(12\) | 만기일 | YYYYMMDD |
| etcList: assetType | String\(8\) | 상품구분자 | BOND\(채권\), CD, CP, DLS, ELS, STB\(사채\), RP\(미구분\), CRP\(약정식RP\), RRP\(수시RP\), WRT\(워런트\) |
| etcList: assetName | String\(15\) | 상품명 |  |
| etcList: isinCode | String\(12\) | . | 현재는 지원 안 함 \(1.0부터 지원예정\) |
| respCode | String\(8\) | 응답코드 |  |
| respMsg | String\(50\) | 응답메시지 |  |





## 계좌잔고 조회 API

조회대상이 되는 계좌의 실제 잔고 수량, 손익, 수익률 등을 상세히 조회하기 위한 API

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/account" path="/balance/search" %}
{% api-method-summary %}
/account/balance/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer 발급받은 access token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{ 
  "commonHeader":{ 
    "reqIdPlatform":"fagbbs22321",
    "reqIdConsumer":" ID00002",
    "certDn":"",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "accInfo":{ 
      "realAccNo":"",
      "vtAccNo":"160678007213500001"
  },
  "balanceResponseBody":{ 
    "queryType":{ 
      "assetType":"ALL",
      "count":"0",
      "page":"null"
    },
    "queryResult":{ 
      "totalCnt":157.0,
      "count":157.0,
      "page":"null"
    }
  },
  "balanceList":{ 
    "balance":{ 
        "summary":{ 
          "cashBalance":6976542.0,
          "d1":6976542.0,
          "d2":6976542.0,
          "substitute":9.816358E7,
          "receivable":0.0,
          "subsMargin":762635.0,
          "loanCredit":0.0,
          "valAtTrade":3.69827563509E11,
          "valueAtCur":3.89165300498E11,
          "proLoss":1.9337736989E10,
          "totalAccVal":3.8917227704E11,
          "cashAvWithdraw":6976542.0
      },
      "equityList":[ 
          { 
            "assetType":"KSP",
            "isinCode":"HK0000050325",
            "qty":120.0,
            "tradeType":"SUM",
            "valAtTrade":281764.0,
            "valAtCur":245400.0,
            "proLoss":-36364.0,
            "earningRate":-12.9
          },
          { 
            "assetType":"KDQ",
            "isinCode":"HK0000054723",
            "qty":1186.0,
            "tradeType":"SUM",
            "valAtTrade":2326871.0,
            "valAtCur":1867950.0,
            "proLoss":-458921.0,
            "earningRate":-19.72
          },
          { 
            "assetType":"KSP",
            "isinCode":"KR7000020008",
            "qty":19.0,
            "tradeType":"SUM",
            "valAtTrade":181519.0,
            "valAtCur":201400.0,
            "proLoss":19881.0,
            "earningRate":10.95
          },
          { 
            "assetType":"KDQ",
            "isinCode":"USU652221081",
            "qty":71.0,
            "tradeType":"SUM",
            "valAtTrade":514957.0,
            "valAtCur":501970.0,
            "proLoss":-12987.0,
            "earningRate":-2.52
          }
        ],
        "fundList":[ 
          { 
            "fundCode":"KRZ500395135",
            "fundName":"삼성중소형FOCUS증권자1호[주식]",
            "valAtTrade":0.0,
            "valAtCur":7.2329965E7,
            "proLoss":7.2329965E7,
            "firstDateBuy":"20160112",
            "lastDateBuy":"20160113",
            "maturity":"00000000",
            "earningRate":-9.58
          },
          { 
            "fundCode":"KRZ500395136",
            "fundName":"삼성중소형FOCUS증권자1호[주식]",
            "valAtTrade":0.0,
            "valAtCur":8747937.0,
            "proLoss":8747937.0,
            "firstDateBuy":"20150820",
            "lastDateBuy":"20150910",
            "maturity":"00000000",
            "earningRate":-12.52
          },          { 
            "fundCode":"KRZ501831185",
            "fundName":"메리츠코리아증권투자신탁1호[주",
            "valAtTrade":0.0,
            "valAtCur":8416030.0,
            "proLoss":8416030.0,
            "firstDateBuy":"20150818",
            "lastDateBuy":"20150819",
            "maturity":"00000000",
            "earningRate":-15.83
          }
        ],
        "etcList":[ 
          { 
            "assetType":"BOND",
            "assetName":"국민주택1종11-07",
            "qty":1.0E10,
            "tradeType":"SUM",
            "valAtTrade":9.438E9,
            "valueAtCur":1.1584E10,
            "earningRate":22.73
          },
          { 
            "assetType":"BOND",
            "assetName":"한국지역난방공사13-1",
            "qty":1.0E10,
            "tradeType":"SUM",
            "valAtTrade":9.992E9,
            "valueAtCur":1.0168E10,
            "earningRate":1.76
          },
          { 
            "assetType":"BOND",
            "assetName":"주택금융공사MBS2016-10(1-4)",
            "qty":1.0E10,
            "tradeType":"SUM",
            "valAtTrade":1.0E10,
            "valueAtCur":1.0145E10,
            "earningRate":1.45
          },
          { 
            "assetType":"BOND",
            "assetName":"주택금융공사MBS2016-7(1-5)",
            "qty":2.0E10,
            "tradeType":"SUM",
            "valAtTrade":2.0E10,
            "valueAtCur":2.0616E10,
            "earningRate":3.08
          },
          { 
            "assetType":"BOND",
            "assetName":"강원도개발공사121",
            "qty":1.0E10,
            "tradeType":"SUM",
            "valAtTrade":1.0E10,
            "valueAtCur":1.0024E10,
            "earningRate":0.24
          },
          { 
            "assetType":"DLS",
            "assetName":"우리투자증권(DLS)1120",
            "qty":5.4E10,
            "tradeType":"SUM",
            "valAtTrade":5.4E10,
            "valueAtCur":5.54094E10,
            "earningRate":2.61
          },
          { 
            "assetType":"ELS",
            "assetName":"NH투자증권(ELB)759",
            "qty":2.0E10,
            "tradeType":"SUM",
            "valAtTrade":2.0E10,
            "valueAtCur":2.05E10,
            "earningRate":2.5
          },
          { 
            "assetType":"CP",
            "assetName":"루카스 20131227-89-2",
            "qty":1.0E9,
            "tradeType":"SUM",
            "valAtTrade":9.91452055E8,
            "valueAtCur":1.0E9,
            "earningRate":0.86
          },
          { 
            "assetType":"CP",
            "assetName":"루카스 20131227-89-6",
            "qty":1.0E9,
            "tradeType":"SUM",
            "valAtTrade":9.91452055E8,
            "valueAtCur":1.0E9,
            "earningRate":0.86
          },
          { 
            "assetType":"CP",
            "assetName":"루카스 20131227-89-7",
            "qty":1.0E9,
            "tradeType":"SUM",
            "valAtTrade":9.91452055E8,
            "valueAtCur":1.0E9,
            "earningRate":0.86
          },
          { 
            "assetType":"CP",
            "assetName":"루카스 20131227-89-12",
            "qty":1.0E9,
            "tradeType":"SUM",
            "valAtTrade":9.91452055E8,
            "valueAtCur":1.0E9,
            "earningRate":0.86
          },
          { 
            "assetType":"CP",
            "assetName":"루카스 20131227-89-14",
            "qty":1.0E9,
            "tradeType":"SUM",
            "valAtTrade":9.91452055E8,
            "valueAtCur":1.0E9,
            "earningRate":0.86
          },
          { 
            "assetType":"CP",
            "assetName":"루카스 20131227-89-15",
            "qty":1.0E9,
            "tradeType":"SUM",
            "valAtTrade":9.91452055E8,
            "valueAtCur":1.0E9,
            "earningRate":0.86
          }
        ]
      }
  },
  "resp":{ 
    "respCode":"200",
    "respMsg":"OK"
  }
}

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{ 
  "partner":{ 
    "comId":"F9999",
    "srvId":"999"
  },
  "commonHeader":{ 
    "reqIdPlatform":"",
    "reqIdConsumer":"ID00002",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "devInfo":{ 
    "ipAddr":"123451234500",
    "macAddr":"7054D27EE247"
  },
"accInfo":{ 
      "vtAccNo":"160678007213500001"
   },
  "balanceRequestBody":{ 
    "queryType":{ 
      "assetType":"ALL",
      "count":0,
      "page":"null"
    }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### **Request Parameters**

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | String\(5\) | 핀테크기업코드 |  |
| srvId | String\(20\) | 핀테크서비스코드 |  |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크기업에서 사용하는 메시지 구분 |  |
| ci | String\(88\) | 연계정보 |  |
| ipAddr | String\(32\) | 사용자 단말 IP주소  | dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정 |
| macAddr | String\(50\) | 사용자 MAC 주소 | PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| assetType | String\(8\) | 요청하는 자산유형 | CASH\(현금\), EQTY\(주식\), FUND\(펀드\), ETC\(기타자산\), ALL\(전체\)인 경우는 page 처리없이 대용량 데이터 전송이 가능한 증권사만 가능 |
| rspType | String\(8\) | 응답 유형 | RAT\(잔고구성비율\)은 기본으로 제공하며, 증권사에 따라 QTY\(실제잔고수량\)도 가능하나 본 API의 목적상 사용을 권장하지 않음 |
| count | Number | 응답 별 최대 응답 건수 | 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 / assetType이 ‘ALL’인 경우는 page없이 일괄전송이므로 본 필드는 의미 없으므로 0으로 설정 |
| page | String\(24\) | 다음 page를 지시하는 키 | 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청 |

{% hint style="success" %}
 `assetType`을 'ALL'로 요청 가능한 증권사    
   : NH투자증권, 대신증권, 키움증권, 신한금융투자
{% endhint %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) | . | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| totalCnt | Number | 조회 조건의 총 메시지 건수 |  |
| count | Number | 현 메시지 내 응답 건수 |  |
| page | String\(24\) | 다음 page 번호 | “null”이면 더 이상 없음 |
| summary | Object | 잔고 요약 | SUM |
| cashBalance | Number | 현금잔고 | 현금잔고 |
| d1 | Number | D+1잔고 |  |
| d2 | Number | D+2잔고 |  |
| substitute | Number | 대용금 |  |
| receivable | Number | 미수/미납금 |  |
| subsMargin | Number | 대용증거금 |  |
| loanCredit | Number | 대출/신용금 |  |
| valAtTrade | Number | 유가증권매수금액 |  |
| valueAtCur | Number | 유가증권평가금액 |  |
| proLoss | Number | 유가증권평가손익 |  |
| totalAccVal | Number | 총평가금액 |  |
| cashAvWithdraw | Number | 출금가능액 |  |
| equityList: assetType | String\(8\) | 상품구분자 | KSP\(코스피\), KDQ\(코스닥\), ETF\(ETF\), FUT\(선물\), OPT\(옵션\), ELW\(ELW\), ETC\(기타\) |
| equityList :isinCode | String\(12\) | ISINCODE\(12\) |  |
| qty | Number | 수량 또는 비중 | equity 내 비중, 소수점 2째자리까지 / 신용 매수 분 포함하고 대출잔고는 반영안함 |
| tradeType | String\(8\) | 잔고구분 | NRM\(일반/현금\), CRD\(신용\), LOAN\(대출\), SUM\(분류가 불가한 경우 구분 없이 합산한 경우며 대출잔고는 제외\) |
| valAtTrade | Number | 매수금액 |  |
| valAtCur | Number | 평가금액 |  |
| proLoss | Number | 평가손익 |  |
| earningRate | Number | 수익률 | 소수점 2째자리까지 |
| fundCode | String\(20\) | 펀드표준코드 |  |
| fundName | Number | 펀드명 | 최대 15자 |
| firstDateBuy | String\(12\) | 최초매수일 | YYYYMMDD |
| lastDateBuy | String\(12\) | 최종매수일 | YYYYMMDD |
| maturity | String\(12\) | 만기일 | YYYYMMDD |
| etcList: assetType | String\(8\) | 상품구분자 | BOND\(채권\), CD, CP, DLS, ELS, STB\(사채\), RP\(미구분\), CRP\(약정식RP\), RRP\(수시RP\), WRT\(워런트\) |
| etcList: assetName | String\(15\) | 상품명 |  |
| etcList: isinCode | String\(12\) | . | 현재는 지원 안 함 \(1.0부터 지원예정\) |
| respCode | String\(8\) | 응답코드 |  |
| respMsg | String\(50\) | 응답메시지 |  |





## 거래내역 조회 API

 조회대상이 되는 계좌의 입금, 출금, 매수, 매도 이력을 조회할 수 있는 API

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/account" path="/transaction/search" %}
{% api-method-summary %}
/account/transaction/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" required=true type="string" %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" required=true type="string" %}
Bearer 발급받은 access token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{ 
  "commonHeader":{ 
    "reqIdPlatform":"2ddacehgg",
    "reqIdConsumer":"ID00003",
    "certDn":"",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "accInfo":{ 
      "realAccNo":"",
      "vtAccNo":"160731060768600001"
  },
  "transactionHistoryResponseBody":{ 
    "queryParams":{ 
      "fromDate":"20160101",
      "toDate":"20160720",
      "isinCode":"",
      "side":"",
      "count":30,
      "page":""
    },
    "queryResult":{ 
      "count":30,
      "page":"201603100000000961",
      "totalCnt":120
    }
  },
  "transList":{ 
    "transaction":[ 
      { 
        "transDate":"20160126",
        "transType":"DEP",
        "isinCode":"",
        "changeAmt":14399400,
        "changeQty":0,
        "qty":0
      },
      { 
        "transDate":"20160126",
        "transType":"ASK",
        "isinCode":"NC30010",
        "changeAmt":-14399400,
        "changeQty":0,
        "qty":0
      },
      { 
        "transDate":"20160202",
        "transType":"DEP",
        "isinCode":"",
        "changeAmt":100,
        "changeQty":0,
        "qty":0
      },
      { 
        "transDate":"20160202",
        "transType":"ETC",
        "isinCode":"",
        "changeAmt":-100,
        "changeQty":0,
        "qty":0
      },
      { 
        "transDate":"20160310",
        "transType":"BID",
        "isinCode":"NC30010",
        "changeAmt":180456840,
        "changeQty":0,
        "qty":0
      },
      { 
        "transDate":"20160310",
        "transType":"WID",
        "isinCode":"",
        "changeAmt":-10000,
        "changeQty":0,
        "qty":0
      },
      { 
        "transDate":"20160310",
        "transType":"WID",
        "isinCode":"",
        "changeAmt":-10500,
        "changeQty":0,
        "qty":0
      }
    ]
  },
  "resp":{ 
    "respCode":"200",
    "respMsg":"OK"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{ 
  "partner":{ 
    "comId":"F9999",
    "srvId":"999"
  },
  "commonHeader":{ 
    "reqIdPlatform":"",
    "reqIdConsumer":"ID00003",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "devInfo":{ 
    "ipAddr":"123456789012",
    "macAddr":"7054D27EE247"
  },
  "accInfo":{ 
      "realAccNo":null,
      "vtAccNo":"160731060768600001"
  },
  "transactionHistoryRequestBody":{ 
    "queryParams":{ 
      "fromDate":"20160101",
      "toDate":"20160720",
      "isinCode":"",
      "side":"",
      "count":30,
      "page":""
    }
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### **Request Parameters**

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | ~~**String\(5\)**~~ | 핀테크기업코드 |  |
| srvId | String\(20\) | 핀테크서비스코드 |  |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크기업에서 사용하는 메시지 구분 |  |
| ci | String\(88\) | 연계정보 |  |
| ipAddr | String\(32\) | 사용자 단말 IP주소  | dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정 |
| macAddr | ~~**String\(50\)**~~ | 사용자 MAC 주소 | PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| queryPrams | Object | 조회범위는 증권사마다 상이 |  |
| fromDate | String\(12\) | 조회시작날짜 | YYYYMMDD |
| toDate | String\(12\) | 조회종료날짜 | YYYYMMDD |
| isinCode | String\(20\) | 조회조건 | 종목코드, 종목코드지정 없으면 전체종목을 대상 |
| side | String\(8\) | 조회조건 | BID\(매도\), ASK\(매수\), DEP\(이체입금\), WID\(이체출금\), 조회조건이 없거나 ‘ALL’이면 전체구분자가 대상 |
| count | Number | 응답 별 최대 응답 건수 | 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 / assetType이 ‘ALL’인 경우는 page없이 일괄전송이므로 본 필드는 의미 없으므로 0으로 설정 |
| page | String\(24\) | 다음 page를 지시하는 키 | 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청 |

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) | . | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| queryResult: totalCnt | Number | 조회 조건의 총 메시지 건수 |  |
| queryResult: count | Number | 현 메시지 내 응답 건수 |  |
| queryResult: page | String\(24\) | 다음 page 번호 | “null”이면 더 이상 없음 |
| queryParams: fromDate | String\(12\) | 조회시작날짜 | YYYYMMDD |
| queryParams: toDate | String\(12\) | 조회종료날짜 | YYYYMMDD |
| queryParams: isinCode | String\(12\) | 조회조건 | 종목코드 |
| queryParams: side | String\(8\) | 조회조건 | BID\(매도\), ASK\(매수\) |
| queryParams: count | Number | 응답 별 건수 | default는 50 |
| queryParams: page | String\(24\) | 다음 page 번 | 응답데이터의 특정 지점을 지정할 경우 \(요청 시 값\) |
| transaction: isinCode | String\(20\) | 종목코드 | 입출금은 CASH로 표기 |
| transaction: transDate | String\(12\) | 거래일자 | YYYYMMDD |
| transaction: transType | String\(8\) | 거래구분 | BID\(매도\), ASK\(매수\), DEP\(이체입금\), WID\(이체출금\) |
| transaction: changeAmt | Number | 금액증감 | 매도/매수/이체에 따른 금액변동 |
| transaction: changeQty | Number | 수량증감 | 매도/매수량, 이체 시는 0 |
| transaction: qty | Number | 잔고수량 | 거래 후 잔량 |
| respCode | String\(8\) | 응답코드 |  |
| respMsg | String\(50\) | 응답메시지 |  |





## 관심종목 조회 API

조회대상이 되는 계좌에 설정된 관심종목을 조회할 수 있는 API

{% api-method method="post" host="https://{APIGWAddr}/v1/{증권사단축명}/account" path="/interest/search" %}
{% api-method-summary %}
/account/interest/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter type="string" required=true name="Content-Type" %}
Application/json
{% endapi-method-parameter %}

{% api-method-parameter type="string" required=true name="Authorization" %}
Bearer 발급받은 access token
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{ 
  "commonHeader":{ 
    "reqIdPlatform":"fs901jjshgs",
    "reqIdConsumer":"ID0000020",
    "certDn":"",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "accInfo":{ 
      "realAccNo":"",
      "vtAccNo":"160731060768600001"
  },
  "interestSymbolListResponseBody":{ 
    "groupList":{ 
      "group":[ 
        { 
          "isinCode":[ 
            "KR7122870009",
            "KR7028260008",
            "KR7001360007",
            "KR7011070000",
            "KR7017800004"
          ],
          "groupName":"관심종목00",
          "modifyDate":""
        },
        { 
          "isinCode":[ 
            "KR7176950004",
            "KR7143860005",
            "KR7138230008",
            "KR7205720006"
          ],
          "groupName":"ETF",
          "modifyDate":""
        }
      ]
    }
  },
  "resp":{ 
    "respCode":"200",
    "respMsg":"OK"
  }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Request Example

{% code-tabs %}
{% code-tabs-item title="Request Body Example" %}
```yaml
{ 
  "partner":{ 
    "comId":"F9999",
    "srvId":"999"
  },
  "commonHeader":{ 
    "reqIdPlatform":"",
    "reqIdConsumer":"ID0000020",
    "ci":" S1V7HGXBV1EPGBJastZf4fQV+eOpOc1pfizByV6UIEEJHM/PF9QKu+PU2OThEog7QmVKSZNibNGg+/k0XB/9jQ=="
  },
  "devInfo":{ 
    "ipAddr":"123456789012",
    "macAddr":"7054D27EE247"
  },
  "accInfo":{ 
      "vtAccNo":"160731060768600001"
  },
  "interestSymbolListRequestBody":{ 
    "queryType":{ 
      "assetType":"",
      "rspType":null,
      "count":0,
      "page":"",
      "totalCnt":0
    }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 **Request Parameters**

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | String\(5\) | 핀테크기업코드 |  |
| srvId | String\(20\) | 핀테크서비스코드 |  |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크기업에서 사용하는 메시지 구분 |  |
| ci | String\(88\) | 연계정보 |  |
| ipAddr | String\(32\) | 사용자 단말 IP주소  | dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정 |
| macAddr | ~~**String\(50\)**~~ | 사용자 MAC 주소 | PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| queryType | Object | . | 지원증권사 : 삼성증권 |
| assetType | String\(8\) | . | EQY\(유가증권/코스닥\) |
| rspType | String\(8\) | . | "" \(값없음\) |
| count | Number | 응답 별 최대 응답 건수 | 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음 / 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함 |
| page | String\(24\) | 다음 page를 지시하는 키 | 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청 |

{% hint style="danger" %}
`queryType`은 삼성증권만 지원되며, 타 증권사는 사용하지 못함
{% endhint %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) | . | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| queryResult: totalCnt | Number | 총 메시지 건수 |  |
| queryResult: count | Number | 메시지 내 응답 건수 |  |
| queryResult: page | String\(24\) | 다음 page 번호 | “null”이면 더 이상 없음 |
| group: groupName | String\(20\) | 관심종목 그룹 이름 |  |
| group: modifyDate | String\(12\) | 최종 수정일 | 선택 |
| group: isinCode | String Array \(각 20\) | 종목코드 |  |
| respCode | String\(8\) | 응답코드 |  |
| respMsg | String\(50\) | 응답메시지 |  |



