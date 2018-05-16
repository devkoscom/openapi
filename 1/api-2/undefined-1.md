# 계좌서비스

계좌기반 조회 API는 증권사별로 호출 URI가 다르나 큰 틀은 동일하며 단지 증권사구분이 URI에 포함되어 있는 구조입니다. 

{% hint style="success" %}
계좌기반 조회 API는[ 개발자센터-계좌조회API​](https://developers.koscom.co.kr/documentation/account) 에서 이용할 수 있습니다
{% endhint %}



#### Syntax

* HTTP methods
  * **POST**
* Authentication
  * **OAuth2**



### 조회 유의사항

 조회는 API에 지정된 가상계좌를 조회범위로 하기 때문에 계좌속성\(위탁, 펀드, 파생상품 등\)에 따라 조회조건이 충족되지 않을 수 있으므로 전 상품군을 대상으로 조회할 경우는 주의가 필요합니다. 예로 보통 증권회사의 종합계좌는 모든 금융상품을 취급할 수 있는 것이지만 경우에 따라 파생상품과 같은 특정 상품군은 별도로 관리되는 증권회사도 있으며, 종합계좌 개념을 도입하지 않는 증권사도 존재합니다. 따라서 종합계좌라고 판단되어 KOSPI200 파생상품 잔고를 조회하였을 때 응답에 해당상품이 반드시 포함될 것이라 판단하고 비즈니스를 설계하면 안됩니다. 

예로 자산포트폴리오조회와 계좌잔고조회의 경우 모든 상품군을 조회범위에 포함하는 ‘ALL’검색조건을 지원하는 증권사의 경우 해당 조건으로 계좌를 조회하면 문제가 없지만, ‘ALL’검색조건을 지원하지 않는 증권사의 경우 각 상품군별로  계좌를 대상으로 조회해야 누락 없이 전 상품군을 조회할 수 있습니다. 



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
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer 발급받은 access token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
 Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="partner" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="commonHeader" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="devInfo" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="accInfo" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="portfolioRequestBody" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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

#### Request Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 |  |
| srvId | string\(20\) | 핀테크 서비스 코드 |  |
| reqIdPlatform | string | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | 선택 |
| ci | string\(88\) | 연계정보  | 88bytes |
| ipAddr | string\(32\) | 사용자 단말 IP주소  | \*테이블 하단 참조 |
| macAddr | string\(50\) | 사용자 MAC주소  | \*테이블 하단 참조 |
| vtAccNo | string\(30\) | 가상계좌번호 |  |
| assetType | String\(8\) | 자산유형 | \*테이블 하단 참조 |
| rspType | String\(8\) | 응답유형 | \*테이블 하단 참조 |
| count | number | 응답별 최대 응답 건수 | \*테이블 하단 참조 |
| page | String\(8\) | 다음page를 지시하는 키 | \*테이블 하단 참조 |

> * ipAddr : IP주소
>   * dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정
> * macAddr : Mac주소
>   * PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정
> * assetType : 요청하는 자산유형
>   * 값: CASH\(현금\), EQTY\(주식\), FUND\(펀드\), ETC\(기타자산\), ALL\(전체\)인 경우는 page 처리없이 대용량 데이터 전송이 가능한 증권사만 가능
> * rspType : 응답 유형
>   * 값은 RAT\(잔고구성비율\)은 기본으로 제공하며, 증권사에 따라 QTY\(실제잔고수량\)도 가능하나 본 API의 목적상 사용을 권장하지 않음
> * count : 응답별 최대 응답 건수
>   * 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음
>   * 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함
>   * assetType이 ‘ALL’인 경우는 page없이 일괄전송이므로 본 필드는 의미 없으므로 0으로 설정
> * page: 다음 page를 지시하는 키
>   * 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청

{% hint style="info" %}
**`assetType`을 ‘ALL’로 요청 가능한 증권사**

: NH투자증권, 대신증권, 키움증권, 신한증권 

주\) 보유비중 조회는 현재 일부 증권사의 경우 값이 부정확한 경우가 있고, 비중대신 수량을 제공하는 경우도 있으므로 주의 필요함. 보유비중은 수익기여도 \(해당 자산군에서 해당종목이 차지하는 수익기여도\)로 산출한 경우가 대부분이며, 증권사별 산출 기준은 추후 게시예정
{% endhint %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | . | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) |  | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| totalCnt | number | 조회 조건의 총 메시지 건수 |  |
| count | number | 현 메시지 내 응답 건수 |  |
| page | string\(24\) | 다음 page 번호 |  “null”이면 더 이상 없음 |
| amt | number | 전체 자산 중 현금잔고 또는 비중  |  |
| assetType | String\(8\) | 상품구분자 | \*테이블 하단 참조 |
| isinCode | String\(20\) | . | 현재는 지원안함 \(1.0부터 지원예정\) |
| qty | number | 수량 또는 비중 | \*테이블 하단 참조  |
| earningRate | number | 수익률 | 소수점 2째자리까지 |
| fundCode | string\(20\) | 펀드표준코드 |  |
| fundName | string\(15\) | 펀드명 | \(최대 15자\) |
| maturity | string\(12\) | 만기일 | YYYYMMDD |
| assetName | string\(15\) | 상품명 |  |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |

> * assetType : 상품구분자
>   * portfolioResponseBody / queryType / assetType
>     * 요청시 설정했던 값이 그대로 전송
>   * portfolio / equityList /assetType
>     *  KSP\(코스피\), KDQ\(코스닥\), ETF\(ETF\), FUT\(선물\), OPT\(옵션\), ELW\(ELW\), ETC\(기타\)
>   * portfolio / etclist / assetType
>     * BOND\(채권\), CD, CP, DLS, ELS, STB\(사채\), RP\(미구분\), CRP\(약정식RP\), RRP\(수시RP\), WRT\(워런트\)
> * qty : 수량 또는 비중 \(equity 내 비중\)
>   * 소수점 2째자리까지 / 신용 매수 분 포함하고 대출잔고는 반영안함





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
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer 발급받은 access token
{% endapi-method-parameter %}

{% api-method-parameter type="string" name="Content-Type" required=true %}
Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="partner" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="commonHeader" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="devInfo" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="accInfo" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="balanceRequestBody" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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

#### Request Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 |  |
| srvId | string\(20\) | 핀테크 서비스 코드 |  |
| reqIdPlatform | string | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | 선택 |
| ci | string\(88\) | 연계정보  | 88bytes |
| ipAddr | string\(32\) | 사용자 단말 IP주소  | \*테이블 하단 참조 |
| macAddr | string\(50\) | 사용자 MAC주소  | \*테이블 하단 참조 |
| vtAccNo | string\(30\) | 가상계좌번호 |  |
| assetType | String\(8\) | 자산유형 | \*테이블 하단 참조 |
| count | number | 응답별 최대 응답 건수 | \*테이블 하단 참조 |
| page | String\(8\) | 다음page를 지시하는 키 | \*테이블 하단 참조 |

> * ipAddr : IP주소
>   * dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정
> * macAddr : Mac주소
>   * PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정
> * assetType : 요청하는 자산유형
>   * 값은: CASH\(현금\), EQTY\(주식\), FUND\(펀드\), ETC\(기타자산\), ALL\(전체\)인 경우는 page 처리없이 대용량 데이터 전송이 가능한 증권사만 가능
> * count : 응답별 최대 응답 건수
>   * 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음
>   * 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함
>   * assetType이 ‘ALL’인 경우는 page없이 일괄전송이므로 본 필드는 의미 없으므로 0으로 설정
> * page: 다음 page를 지시하는 키
>   * 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청

{% hint style="info" %}
**`assetType`을 ‘ALL’로 요청 가능한 증권사**

: NH투자증권, 대신증권, 키움증권, 신한증권
{% endhint %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 |  |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | . | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) |  | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| totalCnt | number | 조회 조건의 총 메시지 건수 |  |
| count | number | 현 메시지 내 응답 건수 |  |
| page | string\(24\) | 다음 page 번호 |  “null”이면 더 이상 없음 |
| summary | object | 잔고요약 | \(SUM\) |
| cashBalance | Number | 현금잔고 |  |
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
| assetType | String\(8\) | 상품구분자 | \*테이블 하단 참조 |
| isinCode | String\(20\) | . | 현재는 지원안함 \(1.0부터 지원예정\) |
| qty | number | 수량 또는 비중 | \*테이블 하단 참조 |
| tradeType | string\(8\) | 잔고 구분 | \*테이블 하단 참조 |
| varAtTrade | number | 매수금액 |  |
| valAtCur | number | 평가금액 |  |
| proLoss | number | 평가손익 |  |
| earningRate | number | 수익률 | 소수점 2째자리까지 |
| fundCode | string\(20\) | 펀드표준코드 |  |
| fundName | string\(15\) | 펀드명 | \(최대 15자\) |
| firstDateBuy | String\(12\) | 최초매수일 | YYYYMMDD |
| lastDateBuy | String\(12\) | 최종매수일 | YYYYMMDD |
| maturity | string\(12\) | 만기일 | YYYYMMDD |
| assetName | string\(15\) | 상품명 |  |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |

> * assetType : 상품구분자
>   * balanceResponseBody / queryType / assetType
>     * SUM\(현금\), EQTY\(주식\), FUND\(펀드\), ETC\(기타자산\), ALL\(전체\)
>   * portfolio / equityList /assetType
>     *  KSP\(코스피\), KDQ\(코스닥\), ETF\(ETF\), FUT\(선물\), OPT\(옵션\), ELW\(ELW\), ETC\(기타\)
>   * portfolio / etcList / assetType
>     * BOND\(채권\), CD, CP, DLS, ELS, STB\(사채\), RP\(미구분\), CRP\(약정식RP\), RRP\(수시RP\), WRT\(워런트\)
> * tradeType : 잔고구분
>   * portfolio / equityList /tradeType && portfolio / etcList / tradeType
>     * NRM\(일반/현금\), CRD\(신용\), LOAN\(대출\), SUM\(분류가 불가한 경우 구분 없이 합산한 경우며 대출잔고는 제외\)
> * qty : 수량 또는 비중 \(equity 내 비중\)
>   * 소수점 2째자리까지 / 신용 매수 분 포함하고 대출잔고는 반영안함





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
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer 발급받은 access token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="partner" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="commonHeader" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="devInfo" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="accInfo" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="transactionHistoryRequestBody" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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

#### Request Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 |  |
| srvId | string\(20\) | 핀테크 서비스 코드 |  |
| reqIdPlatform | string | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | 선택 |
| ci | string\(88\) | 연계정보  | 88bytes |
| ipAddr | string\(32\) | 사용자 단말 IP주소  | \*테이블 하단 참조 |
| macAddr | string\(50\) | 사용자 MAC주소  | \*테이블 하단 참조 |
| vtAccNo | string\(30\) | 가상계좌번호 |  |
| queryPrams | Object | . | 조회범위는 증권사마다 상이 |
| fromDate | String\(12\) | 조회시작날짜 | YYYYMMDD |
| toDate | String\(12\) | 조회종료날짜 | YYYYMMDD |
| isinCode | String\(20\) | 조회조건: 종목코드 | 종목코드지정 없으면 전체종목을 대상 |
| side | String\(8\) | 조회조건 | \*테이블 하단 참조 |
| count | number | 응답별 최대 응답 건수 | \*테이블 하단 참조 |
| page | String\(8\) | 다음page를 지시하는 키 | \*테이블 하단 참조 |

> * ipAddr : IP주소
>   * dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정
> * macAddr : Mac주소
>   * PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정
> * side: 조회조건
>   * BID\(매도\), ASK\(매수\), DEP\(이체입금\), WID\(이체출금\), 조회조건이 없거나 ‘ALL’이면 전체구분자가 대상
> * count : 응답별 최대 응답 건수
>   * 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음
>   * 0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함
> * page: 다음 page를 지시하는 키
>   * 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 |  |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | . | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) |  | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| totalCnt | number | 조회 조건의 총 메시지 건수 |  |
| count | number | 응답 건수 | \*테이블 하단 참조 |
| page | string\(24\) | 다음 page 번호 | \*테이블 하단 참조 |
| fromDate | String\(12\) | 조회시작날짜 | YYYYMMDD |
| toDate | String\(12\) | 조회종료날짜 | YYYYMMDD |
| transaction | Array | 거래 |  |
| isinCode | String\(20\) | 종목코드 | 입출금은 CASH로 표기 |
| qty | number | 잔고수량 | 거래후 잔량 |
| transDate | string\(12\) | 거래일자 | YYYYMMDD |
| transType | string\(8\) | 거래구분 | \*테이블 하단 참조 |
| changeAmt | Number | 금액증감 | 매도/매수/이체에 따른 금액변동 |
| changeQty | Number | 수량증감 | 매도/매수량, 이체 시는 0 |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |

> * count : 응답별 건수
>   * transactionHistoryResponseBody / queryResult / count
>     * 메시지 내 응답 건수
>   * transactionHistoryResponseBody / queryParams / count
>     * 응답 별 건수 \(default는 50\)
>     * 0이면 50건과 동일
> * page
>   * transactionHistoryResponseBody / queryResult / page
>     * 다음 page 번호, “null” 이면 더 이상 없음
>   * transactionHistoryResponseBody / queryParams / page
>     * 응답데이터의 특정 지점을 지정할 경우 \(요청 시 값\)
> * transType : 거래구분
>   * BID\(매도\), ASK\(매수\),DEP\(이체입금\), WID\(이체출금\)





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
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Bearer 발급받은 access token
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
Application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="partner" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="commonHeader" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="devInfo" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="accInfo" type="object" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="interestSymbolListRequestBody" type="object" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
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

#### Request Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| comId | string\(5\) | 핀테크 기업 코드 |  |
| srvId | string\(20\) | 핀테크 서비스 코드 |  |
| reqIdPlatform | string | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | string\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 | 선택 |
| ci | string\(88\) | 연계정보  | 88bytes |
| ipAddr | string\(32\) | 사용자 단말 IP주소  | \*테이블 하단 참조 |
| macAddr | string\(50\) | 사용자 MAC주소  | \*테이블 하단 참조 |
| vtAccNo | string\(30\) | 가상계좌번호 |  |
| assetType | String\(8\) | 자산유형 | EQY\(유가증권/코스닥\) |
| rspType | String\(8\) | 응답유형 | "" \(값없음\) |
| count | number | 응답별 최대 응답 건수 | \*테이블 하단 참조 |
| page | String\(8\) | 다음page를 지시하는 키 | \*테이블 하단 참조 |

> * ipAddr : IP주소
>   * dot없이 3자리를 12자리로 채워서 설정하며, 모바일인 경우 휴대폰번호로 설정하고 dash없이 10자리로 채워서 설정
> * macAddr : Mac주소
>   * PC의 경우 MAC을 : 없이 붙여 12자리로 표현하고, 모바일인 경우 UUID 설정
> * count : 응답별 최대 응답 건수
>   * 증권사는 반드시 이 요청건수에 맞춰 전송할 필요는 없으나, 단일응답에 담기는 데이터는 이 건수를 초과하지 않음
>
>     0을 설정하면 증권사 전송 시스템이 판단한 전송 가능한 적절한 건수로 요청함을 의미함
> * page: 다음 page를 지시하는 키
>   * 첫 요청은 “null”로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청

{% hint style="danger" %}
"`queryType`"은 **삼성증권**만 **지원**되며, 타 증권사는 사용하지 못함
{% endhint %}

#### Response Parameters

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| reqIdPlatform | String\(20\) | 플랫폼에서 사용하는 메시지 구분자 | 사용안함 |
| reqIdConsumer | String\(20\) | 핀테크 기업에서 사용하는 메시지 구분자 |  |
| certDn | String\(256\) | "" | 사용안함 |
| ci | String\(88\) | 연계정보 |  |
| realAccNo | String\(40\) | "" | 사용안함 |
| vtAccNo | String\(30\) | 가상계좌번호 |  |
| totalCnt | number | 총 메시지 건수 |  |
| count | number | 메시지 내 응답 건수 |  |
| page | string\(24\) | 다음 page 번호 |  “null”이면 더 이상 없음 |
| groupName | String\(20\) | 관심종목 그룹 이름 |  |
| modifyDate | String\(12\) | 최종 수정일 |  |
| isinCode | String\(20\) | 종목코드 | String Array\(각 20\) |
| respCode | string\(8\) | 응답코드 참고 |  |
| respMsg | string\(50\) | 응답메세지 참고 |  |





