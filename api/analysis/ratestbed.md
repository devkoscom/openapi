# RA테스트베드 알고리즘

#### 자세한 설명은 [RA테스트베드 알고리즘 운용실적 API 매뉴얼](https://developers.koscom.co.kr/resources/documentation/20170614\_RATestBed\_API.pdf) 을 참조 하세요.

### API 목록

| URI                            | 설명                                              |
| ------------------------------ | ----------------------------------------------- |
| **/v1/ratestbed/algoapi.json** | RA테스트베드 알고리즘 목록을 조회한다.(테스트베드 사전심사를 완료한 알고리즘 대상) |
| **/v1/ratestbed/rateapi.json** | 로보어드바이저 알고리즘 운용계좌의 기준가 및 기간 수익률을 운용계좌별로 조회한다.   |
| **/v1/ratestbed/riskapi.json** | 로보어드바이저 알고리즘 운용계좌의 위험 및 성과지표를 운용계좌별로 조회한다.      |

****

### GET  **/v1/ratestbed/algoapi.json**

RA테스트베드 알고리즘 목록을 조회한다.

#### &#x20;Content-Type | `Application/json; charset=utf-8` <a href="#content-type-or-application-json-charset-utf-8" id="content-type-or-application-json-charset-utf-8"></a>

#### Authentication | **`API Key`** <a href="#authentication-or-api-key" id="authentication-or-api-key"></a>

#### Response Query Parameters

| **항목명**             | **타입** | **한글명**    | **비고**      |
| ------------------- | ------ | ---------- | ----------- |
| algrthSn            | number | 알고리즘번호     |             |
| odrSn               | number | 테스트 회차     |             |
| algrthNm            | string | 알고리즘명      |             |
| hbrdAssetsAt        | string | 국내/해외자산 구분 | 00:국내 99:해외 |
| compositionAssetsAt | string | 주식보유구분     | 1:미보유 2:보유  |

#### Examples

* 알고리즘 목록 조회

```http
GET https://sandbox-apigw.koscom.co.kr/v1/ratestbed/algoapi.json
```

#### Output

```
{
   "paramVO": 
  {
     "siteName": "portal",
     "targetMethod": "algoapi",
     "programId": "mainavg" 
  },
   "listalgo": [ 
    {
       "algrthSn": 18,
       "odrSn": 1,
       "algrthNm": "RA테스트베드",
       "hbrdAssetsAt": "00",
       "compositionAssetsAt": "1" 
    },

    {
       "algrthSn": 19,
       "odrSn": 1,
       "algrthNm": "RA테스트베드",
       "hbrdAssetsAt": "00",
       "compositionAssetsAt": "2" 
    },

    {
       "algrthSn": 20,
       "odrSn": 1,
       "algrthNm": "RA테스트베드",
       "hbrdAssetsAt": "99",
       "compositionAssetsAt": "1" 
    }
    .
    .
    .
  ] 
}
```

### GET  **/v1/ratestbed/rateapi.json**

로보어드바이저 알고리즘 운용계좌의 기준가 및 기간 수익률을 운용계좌별로 조회한다.

#### Content-Type | `Application/json; charset=utf-8` <a href="#content-type-or-application-json-charset-utf-8" id="content-type-or-application-json-charset-utf-8"></a>

#### Authentication | **`API Key`** <a href="#authentication-or-api-key" id="authentication-or-api-key"></a>

#### Request Query Parameters

| 항목명       | 타입     | 설명      | 비고       |
| --------- | ------ | ------- | -------- |
| algrthSn  | number | 알고리즘 번호 | 예) 35    |
| startDate | number | 시작일자    | yyyymmdd |
| endDate   | number | 종료일자    | yyyymmdd |

#### Response Body Parameters

| 항목명                  | 타입                    | 한글명                                       | 비고                         |
| -------------------- | --------------------- | ----------------------------------------- | -------------------------- |
| basicDate            | string                | 기준일                                       | yyyymmdd                   |
| algrthNm             | string                | 알고리즘명                                     |                            |
| odrSn                | number                | 테스트차수                                     |                            |
| invtTyCd             | string                | 유형구분                                      | 01:안정추구형 02:위험중립형 03:적극투자형 |
| sortOrdr             | number                | 계좌순서                                      | 1,2,3                      |
| standardPrice        | string                | 기준가                                       | 예) 1049.31                 |
| fewdayContProfitRate | number                | 전일대비등락폭                                   | 예) -0.05                   |
| dayProfitRate        | number                | 일일수익률                                     | 예) 0.10                    |
| weekProfitRate       | number                | 주간수익률                                     | 예) 0.25                    |
| monProfitRate1       | number                | 1개월수익률                                    | 예) 2.61                    |
| monProfitRate3       | number                | 3개월수익률                                    | 예) 3.85                    |
| monProfitRate6       | number                | 6개월수익률                                    | 예) 5.98                    |
| yearProfitRate1      | number                | 1년수익률                                     | 데이터 없을경우 (null)            |
| yearProfitRate2      | number                | 2년수익률                                     | 데이터 없을경우 (null)            |
| yearProfitRate3      | number                | 3년수익률                                     | 데이터 없을경우 (null)            |
| accumProfitRate      | number                | 누적수익률                                     | 예) 4.93                    |

#### Examples

* 35번 알고리즘의 2017년 6월 1일부터 2017년 6월 10일까지 수익률 정보를 조회

```
GET https://sandbox-apigw.koscom.co.kr/v1/ratestbed/rateapi.json?algrthSn=35&startDate=20170601&endDate=20170610
```

#### Output

```
{
   "listrate": [ 
    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "01",
       "sortOrdr": 1,
       "standardPrice": 1049.31,
       "fewdayContProfitRate": -0.05,
       "dayProfitRate": 1,
       "weekProfitRate": 0.25,
       "monProfitRate1": 2.61,
       "monProfitRate3": 3.85,
       "monProfitRate6": 5.98,
       "yearProfitRate1": null,
       "yearProfitRate2": null,
       "yearProfitRate3": null,
       "accumProfitRate": 4.93 
    },

    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "02",
       "sortOrdr": 1,
       "standardPrice": 1075.42,
       "fewdayContProfitRate": 0.18,
       "dayProfitRate": 1,
       "weekProfitRate": 0.38,
       "monProfitRate1": 3.88,
       "monProfitRate3": 5.69,
       "monProfitRate6": 9.1,
       "yearProfitRate1": null,
       "yearProfitRate2": null,
       "yearProfitRate3": null,
       "accumProfitRate": 7.54 
    },

    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "03",
       "sortOrdr": 1,
       "standardPrice": 1101.02,
       "fewdayContProfitRate": 0.4,
       "dayProfitRate": 1,
       "weekProfitRate": 0.51,
       "monProfitRate1": 5.09,
       "monProfitRate3": 7.46,
       "monProfitRate6": 12.49,
       "yearProfitRate1": null,
       "yearProfitRate2": null,
       "yearProfitRate3": null,
       "accumProfitRate": 10.1 
    }
    .
    .
    .
   ],
   "paramVO": 
  {
     "algrthSn": "35",
     "startDate": "20170601",
     "endDate": "20170610",
     "siteName": "portal",
     "targetMethod": "rateapi",
     "programId": "mainavg" 
  } 
}
```

### GET  v1/ratestbed/riskapi.json

로보어드바이저 알고리즘 운용계좌의 위험 및 성과지표를 운용계좌별로 조회한다.

#### Content-Type | `Application/json; charset=utf-8` <a href="#content-type-or-application-json-charset-utf-8" id="content-type-or-application-json-charset-utf-8"></a>

#### Authentication | **`API Key`** <a href="#authentication-or-api-key" id="authentication-or-api-key"></a>

#### Request Query Parameters

| 항목명       | 한글명     | 비고       |
| --------- | ------- | -------- |
| algrthSn  | 알고리즘 번호 | 예) 35    |
| startDate | 시작일자    | yyyymmdd |
| endDate   | 종료일자    | yyyymmdd |

#### Response Body Parameters

| 항목명               | 한글명   | 비고                         |
| ----------------- | ----- | -------------------------- |
| basicDate         | 기준일   | yyyymmdd                   |
| algrthNm          | 알고리즘명 | 예) RA테스트                   |
| odrSn             | 테스트차수 |                            |
| invtTyCd          | 유형구분  | 01:안정추구형 02:위험중립형 03:적극투자형 |
| sortOrdr          | 계좌순서  | 1,2,3                      |
| periodSe          | 기간구분  | n:n개월  99:연초이후  999:누적     |
| standardDeviation | 표준편차  | 예) 0.04                    |
| betaValue         | 베타    | 예) 0.31                    |
| sharpeRatio       | 샤프지수  | 예) 9.4                     |
| jensensAlpha      | 젠센알파  | 예) 0.07                    |
| inforRate         | 정보비율  | 예) -7.8                    |
| trackingErr       | 트랙킹에러 | 예) 0.07                    |

#### Examples

* 35번 알고리즘의 2017년 6월 1일부터 2017년 6월 10일까지 위험 및 성과지표를 조회

```
GET https://sandbox-apigw.koscom.co.kr/v1/ratestbed/riskapi.json?algrthSn=35&startDate=20170601&endDate=20170610
```

#### Output

```
{
   "paramVO": 
  {
     "algrthSn": "35",
     "startDate": "20170601",
     "endDate": "20170610",
     "siteName": "portal",
     "targetMethod": "riskapi",
     "programId": "mainavg" 
  },
   "listrisk": [ 
    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "01",
       "sortOrdr": 1,
       "periodSe": 1,
       "standardDeviation": 0.04,
       "betaValue": 0.31,
       "sharpeRatio": 9.4,
       "jensensAlpha": 0.07,
       "inforRate": -7.87,
       "trackingErr": 0.07 
    },

    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "01",
       "sortOrdr": 1,
       "periodSe": 3,
       "standardDeviation": 0.03,
       "betaValue": 0.23,
       "sharpeRatio": 4.48,
       "jensensAlpha": 0.02,
       "inforRate": -4.33,
       "trackingErr": 0.08 
    },

    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "01",
       "sortOrdr": 1,
       "periodSe": 6,
       "standardDeviation": 0.03,
       "betaValue": 0.22,
       "sharpeRatio": 3.97,
       "jensensAlpha": 0.02,
       "inforRate": -3.67,
       "trackingErr": 0.07 
    },

    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "01",
       "sortOrdr": 1,
       "periodSe": 99,
       "standardDeviation": 0.03,
       "betaValue": 0.22,
       "sharpeRatio": 3.79,
       "jensensAlpha": 0.01,
       "inforRate": -4.09,
       "trackingErr": 0.07 
    },

    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "01",
       "sortOrdr": 1,
       "periodSe": 999,
       "standardDeviation": 0.03,
       "betaValue": 0.24,
       "sharpeRatio": 2.4,
       "jensensAlpha": 0,
       "inforRate": -2.97,
       "trackingErr": 0.07 
    },

    {
       "basicDate": "20170601",
       "algrthNm": "RA테스트베드",
       "odrSn": 1,
       "invtTyCd": "02",
       "sortOrdr": 1,
       "periodSe": 1,
       "standardDeviation": 0.05,
       "betaValue": 0.45,
       "sharpeRatio": 9.85,
       "jensensAlpha": 0.12,
       "inforRate": -5.95,
       "trackingErr": 0.06 
    }
    .
    .
    .    
  ] 
}
```
