# RA테스트베드 알고리즘

####  RA테스트베드에서 제공하는 'RA테스트베드 알고리즘 운용실적'은 알고리즘이 운용한 포트폴리오의 운용계좌별 운용실적을 제공한다.

####  자세한 설명은 [RA테스트베드 알고리즘 운용실적 API 매뉴얼](https://developers.koscom.co.kr/resources/documentation/20170614_RATestBed_API.pdf) 을 참조 하세요.


# RA테스트베드 Fintech API

## 개요

본 문서는, RA테스트베드가 제공하는 Fintech API 목록을 나열하고, 각 API에 대하여 간단한 개요를 설명한다.

## 구성

RA테스트베드의 Fintech API는 아래와 같이 구성된다.

1. **algoapi (알고리즘 목록)**
   - RA테스트베드 운용심사를 진행 중이거나 완료한  알고리즘 목록을 조회한다.
2. **rateapi (알고리즘 운용실적)**
   {0}. 알고리즘 운용계좌별 기준가, 전일등락폭, 기간별 수익률 등을 운용실적을 조회한다.
3. **riskapi (알고리즘 위험 및 성과지표)**
   {0}. 알고리즘 운용계좌별 기간 표준편차, 샤프지수 등의 위험 및 성과 지표를 조회한다.




## RA테스트베드 알고리즘 운용실적

#### 개요

RA테스트베드 참여 알고리즘 목록과 운용계좌별 수익률, 위험 및 성과지표 등을 조회 한다.

#### 주요 특징

- 알고리즘이 운용한 포트폴리오의 운용계좌별 운용실적을 제공한다.


#### API 목록

1. **/v1/ratestbed/algoapi.json**
   {0}. RA테스트베드 알고리즘 목록을 조회한다.(테스트베드 사전심사를 완료한 알고리즘 대상)
2. **/v1/ratestbed/rateapi.json**
   {0}. 로보어드바이저 알고리즘 운용계좌의 기준가 및 기간 수익률을 운용계좌별로 조회한다.
3. **/v1/ratestbed/riskapi.json**
   {0}. 로보어드바이저 알고리즘 운용계좌의 위험 및 성과지표를 운용계좌별로 조회한다.




## algoapi

RA테스트베드 알고리즘 목록을 조회한다.

#### Response Parameters


| 항목명                 | 한글명        | 비고          |
| ------------------- | ---------- | ----------- |
| algrthSn            | 알고리즘번호     |             |
| odrSn               | 테스트 회차     |             |
| algrthNm            | 알고리즘명      |             |
| hbrdAssetsAt        | 국내/해외자산 구분 | 00:국내 99:해외 |
| compositionAssetsAt | 주식보유구분     | 1:미보유 2:보유  |
|                     |            |             |

#### Examples

- 알고리즘 목록 조회

```
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





## rateapi

로보어드바이저 알고리즘 운용계좌의 기준가 및 기간 수익률을 운용계좌별로 조회한다.

#### Request Parameters

| 항목명       | 한글명     | 비고       |
| --------- | ------- | -------- |
| algrthSn  | 알고리즘 번호 | 예) 35    |
| startDate | 시작일자    | yyyymmdd |
| endDate   | 종료일자    | yyyymmdd |
|           |         |          |

#### Response Parameters

| 항목명                  | 한글명     | 비고                         |
| -------------------- | ------- | -------------------------- |
| basicDate            | 기준일     | yyyymmdd                   |
| algrthNm             | 알고리즘명   |                            |
| odrSn                | 테스트차수   |                            |
| invtTyCd             | 유형구분    | 01:안정추구형 02:위험중립형 03:적극투자형 |
| sortOrdr             | 계좌순서    | 1,2,3                      |
| standardPrice        | 기준가     | 예) 1049.31                 |
| fewdayContProfitRate | 전일대비등락폭 | 예) -0.05                   |
| dayProfitRate        | 일일수익률   | 예) 0.10                    |
| weekProfitRate       | 주간수익률   | 예) 0.25                    |
| monProfitRate1       | 1개월수익률  | 예) 2.61                    |
| monProfitRate3       | 3개월수익률  | 예) 3.85                    |
| monProfitRate6       | 6개월수익률  | 예) 5.98                    |
| yearProfitRate1      | 1년수익률   | 데이터 없을경우 (null)            |
| yearProfitRate2      | 2년수익률   | 데이터 없을경우 (null)            |
| yearProfitRate3      | 3년수익률   | 데이터 없을경우 (null)            |
| accumProfitRate      | 누적수익률   | 예) 4.93                    |
|                      |         |                            |

#### Examples

- 35번 알고리즘의 2017년 6월 1일부터 2017년 6월 10일까지 수익률 정보를 조회

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





## riskapi

로보어드바이저 알고리즘 운용계좌의 위험 및 성과지표를 운용계좌별로 조회한다.

#### Request Parameters

| 항목명       | 한글명     | 비고       |
| --------- | ------- | -------- |
| algrthSn  | 알고리즘 번호 | 예) 35    |
| startDate | 시작일자    | yyyymmdd |
| endDate   | 종료일자    | yyyymmdd |
|           |         |          |

#### Response Parameters

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
|                   |       |                            |

#### Examples

- 35번 알고리즘의 2017년 6월 1일부터 2017년 6월 10일까지 위험 및 성과지표를 조회

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
