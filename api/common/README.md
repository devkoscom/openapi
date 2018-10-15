# 공통 서비스

## **오픈플랫폼 API Gateway 주소**

> `{APIGWAddr}`

**Production**\(상용\)      \|  `apigw.koscom.co.kr`

**Sandbox**\(샌드박스\)  \|  `sandbox-apigw.koscom.co.kr`

## 공통 URI

**URI                              \|**  `https://{APIGWAddr}/{버전정보}/{증권사단축명}/{조회서비스구분 }`

**Endpoint                    \|**  `https://{APIGWAddr}/{버전정보}/{증권사단축명}/`  
API는 버전으로 구분되기 때문에 URI에 버전정보가 포함되어 있습니다.

{% hint style="success" %}
`{APIGWAddr}` : 오픈플랫폼 API Gateway 주소
{% endhint %}

## 증권사단축명 & API 제공여부

> \(’2018.05.31 기준\)

| `증권사명` | `증권사단축명` | `코드` | `API제공여부` |
| :--- | :--- | :--- | :--- |
| 신한금융투자 | SHINHAN | 00002 | 제공 |
| 대신증권 | DAISHIN | 00004 | 제공 |
| 유진투자증권 | EUGENE | 00008 | 제공 |
| 한양증권 | HANYANG | 00009 | 계약완료 |
| 메리츠종합금융증권 | MERITZ | 00010 | 제공 |
| NH투자증권 | NHINVEST | 00012 | 제공 |
| KB투자증권 | KBINVEST | 00017 | 제공 |
| 유안타증권 | YUANTA | 00024 | 제공 |
| SK증권 | SK | 00025 | 제공 |
| 삼성증권 | SAMSUNG | 00030 | 제공 |
| DB투자금융 | DONGBU | 00031 | 제공 |
| 하이투자증권 | HI | 00046 | 계약완료 |
| 미래에셋대우증권 | MIRAEASSETDAEWOO | 00049 | 계약완료 |
| 키움증권 | KIWOOM | 00050 | 계약완료 |
| 이베스트투자증권 | EBEST | 00063 | 제공 |
| 코리아에셋투자증권 | KOREAASSET | 00064 | 계약완료 |

{% hint style="danger" %}
API 제공 증권사, 일정, API 제공 범위 는 증권사의 사정에 따라 변경될 수 있음.
{% endhint %}

{% hint style="info" %}
개발자센터 어플리케이션 등록 및 API 테스트\(인증\) 이용방법은 [이곳](https://koscom.gitbook.io/open-api/how-to-use/devcenter) 에서 확인하세요.
{% endhint %}

