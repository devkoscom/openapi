---
description: Error 처리
---

# Error Code

Error는 금융투자회사, 오픈플랫폼의 시스템 등 여러 위치에서 발생할 수 있으나 `HTTP Response Status Code`와 `Response Body`를 통해 오픈플랫폼 표준 `error code`와 `message`로 전달합니다.



### Error Message Format

| **HTTP Response Status Code** | 4xx ~ 5xx |
| --- | --- | --- |
| **HTTP Response Content-Type** | Application/json; charset=utf-8 |
| **HTTP Response Body** | {"category": "op-exco",  "code": 9011,  "message": "invalid virtual account number.",   "description": "blah blah"} |

> * HTTP Response Body
>   * `category` : 오류 발생 지점.
>   * `code` : 상세 오류 코드
>   * `message` : 상세 오류 메세지
>   * `description` : 추가 정보

### 

### Error Category

| **`Category`** | **`시스템`** |
| --- | --- | --- | --- | --- |
| `op-apim` | 오픈플랫폼 API Gateway Server |
| `op-auth` | 오픈플랫폼 인증 서버 |
| `op-exco` | 오픈플랫폼 증권사 연계 서버 |
| `{증권사명}` | Ex\) saumgsung, Hyundai  |



### Field Data Type

| **`Field`** | **`Data type`** |
| --- | --- | --- | --- | --- |
| **category** | String |
| **code** | Integer |
| **message** | String |
| **description**\(\*optional\) | String |





## Error Code/Message

### Common Error

오픈플랫폼에서 발생하는 공통오류는 HTTP표준 상태 코드와 오류코드를 동일하게 준용

| **`HTTP Response Status Code`** | **`Error Code`** | **`Error Message`** | **`Description`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 400 | 400 | `Bad Request` | 요청 자원에 대한 Parameter, URI Variable, Payload, Content Media-Type이 서버가 요구하는 명세와 다르거나 받아들일 수 없는 경우. |
| 401 | 401 | `Unauthorized` | 클라이언트의 인증 요청이 실패한 경우. \(e.g. API Key, OAuth…\) |
| 403 | 403 | `Forbidden` | API 이용 권한 획득에 실패한 경우. |
| 404 | 404 | `Not Found` | API가 존재하지 않는 경우. |
| 405 | 405 | `Method Not Allowed` | API가 허용하지 않는 HTTP Method 요청의 경우. |
| 406 | 406 | `Not Acceptable` | API가 허용하지 않는 Accept Media-Type 요청의 경우. |
| 408 | 408 | `Request Timeout` | 요청 API의 수행 시간이 기준 시간보다 초과된 경우. |
| 415 | 415 | `Unsupported Media Type` | API가 허용하지 않는 Content-Type 요청의 경우. |
| 500 | 500 | `Internal Server Error` | 플랫폼 내부에서 발생하는 저 수준 오류의 경우. \(\* low-level error는 비즈니스 오류가 아닌, 코드상의 오류를 말함\) |
| 503 | 503 | `Service Unavailable` | 서버가 일시적인 오류이거나 정상적인 서비스가 불가능한 경우. |
| 505 | 505 | `HTTP Version Not Supported` | 지원되지 않는 HTTP 버전으로 요청한 경우. |



### Custom Error

#### A. 오픈플랫폼 인증서버 에러

| **`HTTP Response Status Code`** | **`Error Code`** | **`Error Message`** | **`Description`** |
| --- | --- | --- | --- | --- |
| 401 | 2001 | `Authentication Failed` | 핀테크 서비스 포탈 사용자의 인증에 실패한 경우. |
| 401 | 2002 | `Invalid OTP Key` | OTP Secret Key가 유효하지 않거나 만료된 경우. |
| 401 | 2003 | `Account Locked` | 인증 시도 제한 횟수를 초과하여 계정이 임시 잠김. |
| 403 | 2100 | `Authorization Failed` | API 및 서비스 이용 권한 획득에 실패한 경우. |



#### B. 오픈플랫폼 증권사 연계 서버 에러

| **`HTTP Response Status Code`** | **`Error Code`** | **`Error Message`** | **`Description`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 500 | 3001 | `Bad response trcode` | 금투사로부터 잘못된 TRCODE가 옴 |
| 400 | 3002 | `Unknown api url` | 요청한 금투사 api 연결정보를 찾을 수 없는 경우 |
| 400 | 3003 | `필수 항목 누락` | 필수 항목이 누락된 경우 |
| 500 | 3004 | `network error` | 일시적 network 장애가 발생한 경우 |
| 500 | 3005 | `network timeout` | 금투사 서버로부터 메시지 응답이 지연된 경우 |
| 500 | 3006 | `not found dn` | 요청한 ci로 사용자 dn값을 찾을 수 없을 경우 |
| 500 | 3007 | `not found user` | 요청한 CI로 사용자를 찾을 수 없을 경우 |
| 500 | 3008 | `not found company info` | 요청한 금투사의 정보를 찾을 수 없을 경우 |
| 500 | 3009 | `not found account info` | 실계좌번호를 찾을 수 없을 경우 |
| 500 | 3010 | `expired account` | 요청계좌가 폐기된 계좌일 경우 |
| 500 | 3011 | `Json parsing error` | Json 메시지 규격에 오류가 있을 경우 |
| 500 | 3012 | `Unknown account number` | 요청계좌가 증권사에 존재하지 않을 경우 |
| 500 | 3013 | `Unknown account type` | 등록되지 않은 계좌 유형의 경우 |
| 500 | 3999 | `Unknown error` | 프로그램 내부 에러\(ex : DB에러\) 가 발생했을 경우 |
| 503 | 3600 | `Target Company Service Unavailable` | 금투사 서버가 정상적인 서비스가 불가능한 경우. |



#### C. 증권사 서버 에러

| **`HTTP Response Status Code`** | **`Error Code`** | **`Error Message`** | **`Description`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 500 | 200 | `OK` | 정상 |
| 500 | 4000 | `Mismatch between DN and AccoutNo` | DN과 계좌번호가 서로 불일치 |
| 500 | 4001 | `Account Not Found` | 해당계좌를 찾을 수 없음 |
| 500 | 4002 | `DN Not Found` | DN값을 찾을 수 없음 |
| 500 | 4003 | `Mismatch between CI and AccountNo` | CI와 계좌번호가 서로 불일치 |
| 500 | 4004 | `CI Not Found` | CI값을 찾을 수 없음 |
| 500 | 4005 | `Mismatch between DN and CI` | DN과 CI가 서로 불일치 |
| 500 | 4006 | `Agreement of Financial Information Not Found.` | 정보제공 동의서의 동의 여부 확인 요망 |
| 500 | 5004 | `Failure To Enrol an vtAccNo` {상세한 사유를 대괄호안에 명시} | 플랫폼에서 발급한 가상계좌번호 등록 실패 \(요청방향: 플랫폼-&gt;증권사\) |
| 500 | 5005 | `Failure To Change an vtAccNo`, {상세한 사유를 대괄호안에 명시} | 발급된 가상계좌번호 또는 가상계좌별칭 변경 실패 \(요청방향: 플랫폼-&gt;증권사\) |
| 500 | 5006 | `Failure To Issue an vtAccNo`, {상세한 사유를 대괄호안에 명시} | 증권사로 요청한 가상계좌발급이 실패 \(요청방향: 플랫폼-&gt;증권사\) |
| 500 | 5007 | `Failure To discard an vtAccNo,` {상세한 사유를 대괄호안에 명시} | 가상계좌 폐기요청이 실패 \(요청방향: 증권사-&gt;플랫폼, 플랫폼-&gt;증권사\) |
| 500 | 6001 | `Invalid Asset Type` | 지원하지 않는 상품구분자 |
| 500 | 6002 | `Invalid Rsp Type` | 지원하지 않는 응답유형 \(QTY, RAT이 아닌 값이 요청에 포함된 경우\) |
| 500 | 6003 | `Invalid Page Value` | 존재하지 않는 Page Key값 요청 \(연속조회시 존재하지 않는 Key값\) |
| 500 | 6004 | `Invalid Query Type,` {상세한 사유를 대괄호안에 명시} |  .  |
| 500 | 6005 | `Result Too Many,` {요청한 조회에 대한 결과건수} | 증권사에서 제공 가능한 총 건수 \(연속조회를 포함\)를 초과한 경우 |
| 500 | 6006 | `Date Range Exceeded,` {최대 조회 가능 날짜 수 명시} | 조회 가능한 날짜 범위 초과 |
| 500 | 6007 | `Invalid Isincode` | 존재하지 않는 isincode로 조회요청 |
| 500 | 6008 | `Invalid Side Type` | 잘못된 거래구분 조회조건, BID, ASK, DEP, WID, ALL 이 아닌 값으로 조회 |
| 500 | 7000 | `Bad Request,` {상세한 사유를 대괄호안에 명시} | 요청에서 무엇이 문제인지 사유 명시 필요 |



