# 계좌서비스

계좌기반 조회 API는 증권사별로 호출 URI가 다르나 큰 틀은 동일하며 단지 증권사구분이 URI에 포함되어 있는 구조입니다. 

API는 버전으로 구분되기 때문에 URI에 버전정보가 포함되어 있습니다. 

#### **URI구조**

* 전체 URI - `https://APIgateway주소/버전정보/증권사단축명/조회서비스구분  `
* Endpoint – `https://APIgateway주소/버전정보/증권사단축명/  `

#### **오픈플랫폼 API gateway 주소**

* Production – `https://apigw.koscom.co.kr  `
* Sandbox – `https://sandbox-apigw.koscom.co.kr  `

{% hint style="success" %}
계좌기반 조회 API에 대한 **자세한 설명**과 **사용방법**은 아래의 [링크](https://developers.koscom.co.kr/documentation/account)를 클릭하면 이용할 수 있습니다:

[​개발자센터-계좌조회API​](https://developers.koscom.co.kr/documentation/account)
{% endhint %}



### 조회 유의사항

 조회는 API에 지정된 가상계좌를 조회범위로 하기 때문에 계좌속성\(위탁, 펀드, 파생상품 등\)에 따라 조회조건이 충족되지 않을 수 있으므로 전 상품군을 대상으로 조회할 경우는 주의가 필요합니다. 예로 보통 증권회사의 종합계좌는 모든 금융상품을 취급할 수 있는 것이지만 경우에 따라 파생상품과 같은 특정 상품군은 별도로 관리되는 증권회사도 있으며, 종합계좌 개념을 도입하지 않는 증권사도 존재합니다. 따라서 종합계좌라고 판단되어 KOSPI200 파생상품 잔고를 조회하였을 때 응답에 해당상품이 반드시 포함될 것이라 판단하고 비즈니스를 설계하면 안됩니다. 

예로 자산포트폴리오조회와 계좌잔고조회의 경우 모든 상품군을 조회범위에 포함하는 ‘ALL’검색조건을 지원하는 증권사의 경우 해당 조건으로 계좌를 조회하면 문제가 없지만, ‘ALL’검색조건을 지원하지 않는 증권사의 경우 각 상품군별로  계좌를 대상으로 조회해야 누락 없이 전 상품군을 조회할 수 있습니다. 



## 증권사단축명 & API 제공여부

> \(’2017.05.30 기준\)

| **`증권사명 `** | **`단축명 `** | **`코드 `** | **`API제공여부`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 교보증권 | KYOBO | 00001 | 미제공\(미정\) |
| 신한금융투자 | SHINHAN | 00002 | 제공 |
| 한국투자증권 | KOREAINVEST | 00003 | 제공 |
| 대신증권 | DAISHIN | 00004 | 제공 |
| 대우증권 | DAEWOO | 00005 | 미제공\(미정\) |
| 신영증권 | SHINYOUNG | 00006 | 미제공\(미정\) |
| 유진투자증권 | EUGENE | 00008 | 제공 |
| 한양증권 | HANYANG | 00009 | 미제공\(예정\) |
| 메리츠종합금융증권 | MERITZ | 00010 | 미제공\(예정\) |
| NH투자증권 | NHINVEST | 00012 | 제공 |
| 부국증권 | BOOKOOK | 00013 | 미제공\(예정\) |
| KB투자증권 | KBINVEST | 00017 | 제공 |
| 한화투자증권 | HANWHA | 00021 | 미제공\(미정\) |
| 에이치엠씨투자증권 | HMC | 00022 | 미제공\(미정\) |
| 유화증권 | YUWHA | 00023 | 미제공\(미정\) |
| 유안타증권 | YUANTA | 00024 | 제공 |
| SK증권 | SK | 00025 | 제공 |
| 골든브릿지투자증권 | GBRIDGE | 00029 | 미제공\(계획중\) |
| 삼성증권 | SAMSUNG | 00030 | 제공 |
| 동부증권 | DONGBU | 00031 | 제공 |
| ~~케이비투자증권~~ | ~~KB~~ | ~~00034~~ | ~~미제공\(계획중\)~~ |
| 하이투자증권 | HI | 00046 | 제공 |
| 미래에셋증권 | MIRAEASSET | 00049 | 미제공\(미정\) |
| 키움증권 | KIWOOM | 00050 | 미제공\(예정\) |
| 리딩투자증권 | LEADING | 00052 | 미제공\(미정\) |
| 하나금융투자 | HANA | 00056 | 미제공\(미정\) |
| 이베스트투자증권 | EBEST | 00063 | 제공 |
| 코리아에셋투자증권 | KOREAASSET | 00064	 | 미제공\(계획중\) |
| 비엔지증권 | BNG | 00065 | 미제공\(계획중\) |
| 흥국증권 | HEUNGKUK | 00066 | 미제공\(계획중\) |
| IBK투자증권 | IBK | 00068 | 미제공\(계획중\) |
| 바로투자증권 | BAROFN | 00069 | 미제공\(계획중\) |
| 토러스투자증권 | TAURUS | 00070 | 미제공\(계획중\) |
| KTB투자증권 | KTB	 | 00071 | 미제공\(계획중\) |
| 엘아이지투자증권 | LIG | 00072 | 미제공\(계획중\) |
| 애플투자증권 | APPLE | 00073 | 미제공\(계획중\) |
| 비엔케이투자증권 | BNKFN | 00086 | 미제공\(계획중\) |

{% hint style="danger" %}
 API 제공 증권사, 일정, API 제공 범위는 증권사의 사정에 따라 변경될 수 있음
{% endhint %}









## 자산 포트폴리오 조회 API

조회대상이 되는 계좌의 실제 잔고 수량, 투자금액 대신 금융투자 상품의 구성비만을 제공함으로써 개인금융정보의 노출부담을 최소화하면서도 투자자산을 기초로 자산통합관리, 자문, 정보제공 등을 받을 수 있도록 하기 위한 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/account" path="/portfolio/search" %}
{% api-method-summary %}
/account/portfolio/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
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

#### Syntax

* URI

  *  /account/portfolio/search

* HTTP methods

  * POST

* Format

  * JSON &lt;application/json; charset=utf-8&gt;

* Content-Type

  * Application/json

* Authentication
  * OAuth 2- Authorization
  * header – Authorization: Bearer 발급받은 access token

#### Example

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

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

 자세한 포맷은 [개발자센터](https://developers.koscom.co.kr/documentation/common/member) 또는 [공식매뉴얼](https://developers.koscom.co.kr/documentation/reference) 에서 확인하세요.

 [​개발자센터-계좌조회API​](https://developers.koscom.co.kr/documentation/account)







## 계좌잔고 조회 API

조회대상이 되는 계좌의 실제 잔고 수량, 손익, 수익률 등을 상세히 조회하기 위한 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/account" path="/balance/search" %}
{% api-method-summary %}
/account/balance/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Syntax

* URI

  * /account/balance/search

* HTTP methods

  * POST

* Format

  * JSON &lt;application/json; charset=utf-8&gt;

* Content-Type

  * Application/json

* Authentication
  * OAuth 2- Authorization
  * header – Authorization: Bearer 발급받은 access token

#### Example

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

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

 자세한 포맷은 [개발자센터](https://developers.koscom.co.kr/documentation/common/member) 또는 [공식매뉴얼](https://developers.koscom.co.kr/documentation/reference) 에서 확인하세요.

 [​개발자센터-계좌조회API​](https://developers.koscom.co.kr/documentation/account)







## 거래내역 조회 API

 조회대상이 되는 계좌의 입금, 출금, 매수, 매도 이력을 조회할 수 있는 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사단축명/account" path="/transaction/search" %}
{% api-method-summary %}
/account/transaction/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Syntax

* URI

  * /account/transaction/search

* HTTP methods

  * POST

* Format

  * JSON &lt;application/json; charset=utf-8&gt;

* Content-Type

  * Application/json

* Authentication
  * OAuth 2- Authorization
  * header – Authorization: Bearer 발급받은 access token

#### Example

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

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

 자세한 포맷은 [개발자센터](https://developers.koscom.co.kr/documentation/common/member) 또는 [공식매뉴얼](https://developers.koscom.co.kr/documentation/reference) 에서 확인하세요.

 [​개발자센터-계좌조회API​](https://developers.koscom.co.kr/documentation/account)







## 관심종목 조회 API

조회대상이 되는 계좌에 설정된 관심종목을 조회할 수 있는 API

{% api-method method="post" host="https://sandbox-apigw.koscom.co.kr/v1/증권사이름/account" path="/interest/search" %}
{% api-method-summary %}
/account/interest/search
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Syntax

* URI

  * /account/interest/search

* HTTP methods

  * POST

* Format

  * JSON &lt;application/json; charset=utf-8&gt;

* Content-Type

  * Application/json

* Authentication
  * OAuth 2- Authorization
  * header – Authorization: Bearer 발급받은 access token

#### Example

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

{% code-tabs %}
{% code-tabs-item title="Response Body Example" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

 자세한 포맷은 [개발자센터](https://developers.koscom.co.kr/documentation/common/member) 또는 [공식매뉴얼](https://developers.koscom.co.kr/documentation/reference) 에서 확인하세요.

 [​개발자센터-계좌조회API​](https://developers.koscom.co.kr/documentation/account)

