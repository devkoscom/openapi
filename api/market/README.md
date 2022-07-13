# 시세 서비스 v2 (종료)



{% hint style="warning" %}
시세라이센스 정책에 따라 기존의 API v2는 **v3으로 업데이트**되었으니 참고해주시길 바랍니다.
{% endhint %}



## Open API 시세 정보

&#x20;다양한 금융시장정보의 실시간 및  과거데이터를 이용하기 편한 **Restul API** 서비스로 제공

#### 자세한 설명은 아래 문서를 참조 하세요.

{% file src="../../.gitbook/assets/OPEN_API_Marketdata_SPEC_V3_11__20200720.xlsx" %}



## API  URI

| **구분** | **Name**                     | **URI**                                                         |
| ------ | ---------------------------- | --------------------------------------------------------------- |
| 시세표    | 주식시장별 현재가리스트                 | /v2/market/multiquote/stocks/{marketcode}/lists                 |
| 시세표    | 주식시장별 시고저 현재가리스트&#xD;        | /v2/market/multiquote/stocks/{marketcode}/ohlclists&#xD;        |
| 시세표    | 주식 복수종목 현재가&#xD;             | /v2/market/multiquote/stocks/{marketcode}/price&#xD;            |
| 시세표    | 주식 복수종목 호가잔량&#xD;            | /v2/market/multiquote/stocks/{marketcode}/orderbook&#xD;        |
| 주식     | 주식 종목 리스트&#xD;               | /v2/market/stocks/{marketcode}/lists&#xD;                       |
| 주식     | 주식 종목 마스터&#xD;               | /v2/market/stocks/{marketcode}/{issuecode}/master&#xD;          |
| 주식     | 주식 종목 마스터(요구형)&#xD;          | /v2/market/stocks/{marketcode}/{issuecode}/selectivemaster&#xD; |
| 주식     | 주식 실시간(요구형)&#xD;             | /v2/market/stocks/{marketcode}/{issuecode}/selectivereal&#xD;   |
| 주식     | 주식 종목 종가&#xD;                | /v2/market/stocks/{marketcode}/{issuecode}/closeprice&#xD;      |
| 주식     | 주식 종목 체결&#xD;                | /v2/market/stocks/{marketcode}/{issuecode}/price&#xD;           |
| 주식     | 주식 종목 호가잔량(LP호가제외)&#xD;      | /v2/market/stocks/{marketcode}/{issuecode}/orderbook&#xD;       |
| 주식     | 주식 종목별 투자자별 종가&#xD;          | /v2/market/stocks/{marketcode}/{issuecode}/investors&#xD;       |
| 주식     | KOSPI/KOSDAQ지수 투자자 마감정보&#xD; | /v2/market/stocks/{marketcode}/investors&#xD;                   |
| 주식     | KOSPI/KOSDAQ지수&#xD;          | /v2/market/stocks/{marketcode}/index&#xD;                       |
| 주식     | 주식종목(ETF) 장마감후 순자산가치&#xD;    | /v2/market/stocks/{marketcode}/{issuecode}/closenav&#xD;        |
| 주식     | 주식 공매도 일별조회&#xD;             | /v2/market/stocks/{marketcode}/{issuecode}/shortsell&#xD;       |
| 주식     | 주식 종목 일중&#xD;                | /v2/market/stocks/{marketcode}/{issuecode}/intraday&#xD;        |
| 주식     | 주식 거래상위 회원사 정보&#xD;          | /v2/market/stocks/{marketcode}/{issuecode}/traderaking&#xD;     |
| 주식     | 주식 외국인 보유율 히스토리&#xD;         | /v2/market/stocks/{marketcode}/{issuecode}/foreignhistory&#xD;  |
| 주식     | 주식 종목 히스토리&#xD;              | /v2/market/stocks/{marketcode}/{issuecode}/history&#xD;         |
| 선물     | 상품/지수선물 종목 리스트               | /v2/market/futures/{marketcode}/lists&#xD;                      |
| 선물     | 상품/지수선물 종목 마스터               | /v2/market/futures/{marketcode}/{issuecode}/master&#xD;         |
| 선물     | 상품/지수선물 종목 종가                | /v2/market/futures/{marketcode}/{issuecode}/closeprice&#xD;     |
| 선물     | 상품/지수선물\_체결                  | /v2/market/futures/{marketcode}/{issuecode}/price&#xD;          |
| 선물     | 상품/지수선물\_우선호가                | /v2/market/futures/{marketcode}/{issuecode}/orderbook&#xD;      |
| 선물     | 상품/지수선물 투자자별 매매동향            | /v2/market/futures/{marketcode}/market/investors                |
| 선물     | 상품/지수선물 일중&#xD;              | /v2/market/futures/{marketcode}/{issuecode}/intraday&#xD;       |
| 선물     | 상품/지수선물 종목 히스토리&#xD;         | /v2/market/futures/{marketcode}/{issuecode}/history&#xD;        |
| 옵션     | 상품/지수 옵션 종목 리스트&#xD;         | /v2/market/options/{marketcode}/lists&#xD;                      |
| 옵션     | 상품/지수 옵션 종목 마스터&#xD;         | /v2/market/options/{marketcode}/{issuecode}/master&#xD;         |
| 옵션     | 상품/지수 옵션 종목 종가&#xD;          | /v2/market/options/{marketcode}/{issuecode}/closeprice&#xD;     |
| 옵션     | 상품/지수 옵션\_체결&#xD;            | /v2/market/options/{marketcode}/{issuecode}/price&#xD;          |
| 옵션     | 상품/지수 옵션\_우선호가&#xD;          | /v2/market/options/{marketcode}/{issuecode}/orderbook&#xD;      |
| 옵션     | 상품/지수옵션 투자자별 매매동향            | /v2/market/options/{marketcode}/market/investors                |
| 옵션     | 상품/지수 옵션 일중&#xD;             | /v2/market/options/{marketcode}/{issuecode}/intraday&#xD;       |
| 옵션     | 상품/지수 옵션 종목 히스토리&#xD;        | /v2/market/options/{marketcode}/{issuecode}/history&#xD;        |
| 업종     | 업종 종가&#xD;                   | /v2/market/index/{marketcode}/{issuecode}/closeindex&#xD;       |
| 업종     | 업종 지수&#xD;                   | /v2/market/index/{marketcode}/{issuecode}/index&#xD;            |
| 업종     | 업종 예상지수&#xD;                 | /v2/market/index/{marketcode}/{issuecode}/prospectindex&#xD;    |
| 업종     | 업종 시가총액&#xD;                 | /v2/market/index/{marketcode}/{issuecode}/marketcap&#xD;        |
| 업종     | 업종 투자자별&#xD;                 | /v2/market/index/{marketcode}/{issuecode}/investors&#xD;        |
| 업종     | 업종 일중&#xD;                   | /v2/market/index/{marketcode}/{issuecode}/intraday&#xD;         |
| 업종     | 업종 히스토리&#xD;                 | /v2/market/index/{marketcode}/{issuecode}/history&#xD;          |



## API  Summary

| **Name**                     | **Time**      | **Description**                                                  |
| ---------------------------- | ------------- | ---------------------------------------------------------------- |
| 종목별 실시간상세 (유가+코스닥)           | 실시간           | 선택종목(호가+체결:100종목/200종목)에 대한 상세 체결/호가                             |
| 유가증권 전종목실시간                  | 실시간           | 유가증권 시장 전종목 단순 체결(체결가, 체결량, 시간)                                  |
| 코스닥 전종목실시간                   | 실시간           | 코스닥 시장 전종목 단순 체결(체결가, 체결량, 시간)                                   |
| 주식시장별 현재가리스트                 | 실시간           | 시장별 전종목 스냅샷 시세(현재가 기준, 데이타생성주기 1초)&#xD;                          |
| 주식시장별 시고저 현재가리스트&#xD;        | 실시간           | 시장별 전종목 스냅샷 시세(시가,고가,저가,현재가, 데이타생성주기 1초)&#xD;                    |
| 주식 복수종목 현재가&#xD;             | 실시간           | 복수종목(최대 20종목)에 대한 실시간 현재가 조회 &#xD;                               |
| 주식 복수종목 호가잔량&#xD;            | 실시간           | 복수종목(최대 20종목)에 대한 실시간 호가잔량 조회 &#xD;                              |
| 주식 종목 리스트&#xD;               | 6:30          | 종목리스트                                                            |
| 주식 종목 마스터&#xD;               | 6:30          | 종목배치                                                             |
| 주식 종목 마스터(요구형)&#xD;          | 6:30          | 종목배치-종목별 고객이 요구하는 항목만 조회 결과로 전송함&#xD;                            |
| 주식 종목 종가&#xD;                | 전일,당일 15:40이후 | 종목 당일 종가제공&#xD;                                                  |
| 주식 종목 체결&#xD;                | 실시간           | 종목\_체결&#xD;                                                      |
| 주식 종목 호가잔량(LP호가제외)&#xD;      | 실시간           | 종목\_호가잔량\_LP호가\_제외&#xD;                                          |
| 주식 종목별 투자자별 종가&#xD;          | 전일,당일 15:30이후 | 종목별투자자별 종가&#xD;                                                  |
| KOSPI/KOSDAQ지수 투자자 마감정보&#xD; | 전일,당일 15:40이후 | KOSPI/KOSDAQ 투자자 마감정보(업종-투자자별 참고)&#xD;                           |
| KOSPI/KOSDAQ지수&#xD;          | 실시간           | KOSPI/KOSDAQ 실시간 지수&#xD;                                         |
| 주식종목(ETF) 장마감후 순자산가치&#xD;    | 전일,당일 16:00이후 | ETF 종목에 대한 NAV (해외ETF종목 Nav는 환율/기초자산 변동시 조회시점에 따라 다른값이 조회됨)&#xD; |
| 주식 공매도 일별조회&#xD;             | 전일,당일 18:00이후 | 18시 이후 제공&#xD;                                                   |
| 주식 종목 일중&#xD;                | 실시간           | 종목 일중 데이터 제공 (10초, 1분, 10분단위 시/고/저/종)&#xD;                       |
| 주식 거래상위 회원사 정보&#xD;          | 실시간           | 종목 매수/매도 상위 5개 회원사 정보&#xD;                                       |
| 주식 외국인 보유율 히스토리&#xD;         | 6:30          | 종목 외국인 보유율 과거 데이터 제공&#xD;                                        |
| 주식 종목 히스토리&#xD;              | 6:30          | 종목 일별 과거 데이터 제공&#xD;                                             |
| 상품/지수선물 종목 리스트               | 6:30          | 종목리스트                                                            |
| 상품/지수선물 종목 마스터               | 6:30          | 선물 종목에 대한 기초 자료 제공&#xD;                                          |
| 상품/지수선물 종목 종가                | 15:50         | 선물 당일 종가제공&#xD;                                                  |
| 상품/지수선물\_체결                  | 실시간           | 데이터 발생시마다 실시간 제공&#xD;                                            |
| 상품/지수선물\_우선호가                | 실시간           | 데이터 발생시마다 실시간 제공&#xD;                                            |
| 상품/지수선물 일중&#xD;              | 실시간           | 상품/지수선물 일중 데이터 제공 (10초, 1분, 10분단위 시/고/저/종)&#xD;                  |
| 상품/지수선물 종목 히스토리&#xD;         | 6:30          | 상품/지수선물 종목 일별 과거데이터 제공(연결선물코드표 참)&#xD;                           |
| 상품/지수 옵션 종목 리스트&#xD;         | 6:30          | 종목리스트                                                            |
| 상품/지수 옵션 종목 마스터&#xD;         | 6:30          | 옵션 종목에 대한 기초 자료 제공&#xD;                                          |
| 상품/지수옵션 종목 종가&#xD;           | 전일,당일 15:50이후 | 옵션 당일 종가제공&#xD;                                                  |
| 상품/지수옵션\_체결&#xD;             | 실시간           | 데이터 발생시마다 실시간 제공&#xD;                                            |
| 상품/지수옵션\_우선호가&#xD;           | 실시간           | 데이터 발생시마다 실시간 제공&#xD;                                            |
| 상품/지수옵션 일중&#xD;              | 실시간           | 상품/지수옵션 데이터 제공 (10초, 1분, 10분단위 시/고/저/종)&#xD;                     |
| 상품/지수옵션 종목 히스토리&#xD;         | 6:30          | 상품/지수옵션 종목 일별 과거 데이터 제공&#xD;                                     |
| 업종 종가&#xD;                   | 전일,당일 15:40이후 | 업종 당일 종가제공&#xD;                                                  |
| 업종 지수&#xD;                   | 실시간           | 전체 업종지수(KOSPI/KOSDAQ지수 포함)&#xD;                                  |
| 업종 예상지수&#xD;                 | 실시간           | 전체 업종예상지수(KOSPI/KOSDAQ지수 포함)&#xD;                                |
| 업종 시가총액&#xD;                 | 실시간           | 전체 업종시가총액(KOSPI/KOSDAQ지수 포함)&#xD;                                |
| 업종 투자자별&#xD;                 | 실시간           | 전체 업종 투자자별(KOSPI/KOSDAQ지수 포함)&#xD;                               |
| 업종 일중&#xD;                   | 실시간           | 전체 업종 일중 데이터 제공 (10초, 1분, 10분단위 시/고/저/종)&#xD;                    |
| 업종 히스토리&#xD;                 | 6:30          | 전체 업종 일별 과거 데이터 제공(KOSPI/KOSDAQ지수 포함)&#xD;                       |



