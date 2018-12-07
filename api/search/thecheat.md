# 금융사기 피해이력 조회



## 개요

**더치트\(THECHEAT\)는 국내 최초의 집단지성을 활용한 금융사기방지 서비스이다. 실제 피해자로 부터 피해정보를 수집하여, 2차 피해 방지 및 피해 회복을 목표로 하고 있다.**  

### 금융사기 피해이력 조회 API

본 API는 회원의 연락처 또는 계좌번호에 대한 금융사기 이력 존재 여부를 확인하여 2차 피해를 방지하는 것을 목적으로 한다. API를 통해 조회 가능한 정보는 최근 3개월 내에 더치트에 등록된 피해정보를 기준으로 한다. 더치트에 2건 이상의 정보가 등록된 경우 실시간으로 조회 가능하고, 1건 등록된 정보는 검증 및 소명절차를 위해 3일 후 조회 가능하다.

#### 주요 특징

식별정보에 해당하는 연락처 또는 계좌번호의 숫자 정보만으로 조회한다. ​

### POST  /v1/thecheat/fraudsearch

#### **Content-Type \|** `application/json: charset=UTF-8`

#### **Authentication \|** `APIKey`

#### **Request Body** Parameters

| Name | Type | **Description** |
| :--- | :--- | :--- |
| keyword | string | 검색 키워드 - 연락처 또는 계좌 번호 \(숫자만 전달\) |
| keyword\_type | string | 검색 키워드 유형 \(연락처 : phone, 계좌번호 : account, 자동 : auto, 권장하지 않음\) |
| access\_type | string | 조회 유형 - 사용자 검색 : user \(고객이 직접 검색 시\) , 서비스 검색 : service \(SMS, 계좌 인증 등 백그라운드 검색 시\) |
| add\_info | string | `선택` 여분 필드 |

#### **Response Body** Parameters

| Name | Type | **Description** |
| :--- | :--- | :--- |
| result\_code | string | 상태 코드 \(정상 : 1, 그 외 : 실패\) |
| keyword | string | 검색 키워드 |
| keyword\_type | string | 검색 키워드 유형 |
| caution | string | 검색 결과 \(피해사례 등록 여부, Y 또는 N\) |
| access\_type | string | 조회 유형 |
| add\_info | string | 여분필드 |
| result\_msg | string | 결과 메시지 \(오류 메시지 반환\) |

#### **Examples**

```text
POST https://sandbox-apigw.koscom.co.kr/v1/thecheat/fraudsearch
Content-Type: application/json; charset=utf-8

{
	"keyword":"01000000000",
	"keyword_type":"phone",
	"access_type":"user",
	"add_info":""
}
```

* '010-0000-0000' **전화번호**에 대한 피해이력이 있는지 **백그라운드**에서 검색 시

  ```text
  {
    "keyword":"0100000000",
    "keyword_type":"phone",
    "access_type":"service",
    "add_info":""
  }
  ```

* '000000-00-000000' **계좌번호**에 대한 피해이력이 있는지 **고객**이 직접 검색 시

  ```text
  {
    "keyword":"00000000000000",
    "keyword_type":"account",
    "access_type":"user",
    "add_info":""
  }
  ```

#### **Output**

```text
{
   "result_msg": "success",
   "result_code": 1,
   "content": "
  {
    \"keyword\":\"01000000000\",
    \"keyword_type\":\"phone\",
    \"caution\":\"N\",
    \"access_type\":\"user\",
    \"add_info\":
    {
      \"com_id\":\"F0995\"
    }
  }" 
}
```

#### **Result Code**

| 구분 | 결과 | 내용 | 비고 |
| :--- | :--- | :--- | :--- |
| 피혜사례 검색 결과 | 1 | 정상 |  |
|  | -1 | DB 접속 오류 |  |
|  | -2 | 허용된 IP가 아님 |  |
|  | -3 | 유효한 정보 아님 |  |

