# 시세 서비스 v3 (라이센스별)

## 시세 서비스 이용 안내

샌드박스 환경에서 제공되는 시세 데이터는 개발 지원용으로만 제공됩니다.

&#x20;현재 코스콤에서 제공되는 실시간 제공 시세와 자료가 상이할 수 있으며, 제공되는 서비스는 시스템 점검등으로 별도 고지 없이 중단될 수 있습니다.

&#x20;또한, 개발 지원용 시세 데이터라 할지라도 데이터의 가공 또는 축적을 위해서는 코스콤의 정보시세 라이센스가 필요한 것으로써 계약이 수반되어야 시세 데이터의 가공 또는 축적이 가능합니다.

&#x20;오픈API플랫폼 '정보시세 라이센스' 관련 문의는 코스콤 시장정보영업팀 이상원 수석 (이메일 : [success@koscom.co.kr](mailto:success@koscom.co.kr), tel : 02-767-7574)에게 문의 하시면 신속하게 답변 드리겠습니다.

{% content-ref url="../../how-to-use/procedure/charge.md" %}
[charge.md](../../how-to-use/procedure/charge.md)
{% endcontent-ref %}

## Open API 시세 라이센스 정보

&#x20;다양한 금융시장정보의 실시간 및  과거데이터를 이용하기 편한 **Restful API** 서비스로 제공

#### 자세한 설명은  [정보시세데이터\_정의서 V3.11](https://developers.koscom.co.kr/resources/documentation/OPEN\_API\_Marketdata\_SPEC\_V3\_11\_\_20200720.xlsx) 를 참조 하세요.



## API  URI

| **대분** | **시세 라이센스 구분** | **API Name**                      | **API URI**                                                                 |
| ------ | -------------- | --------------------------------- | --------------------------------------------------------------------------- |
| 주식     | 주식실시간종가A       | KOSPI 주식 종목 리스트                   | `/v3/market/closed/kospi/lists`                                             |
| 주식     | 주식실시간종가A       | KOSPI 주식 종목 마스터                   | `/v3/market/closed/kospi/{issuecode}/master`                                |
| 주식     | 주식실시간종가A       | KOSPI 주식 종목 마스터(요구형)              | `/v3/market/closed/kospi/{issuecode}/selectivemaster`                       |
| 주식     | 주식실시간종가A       | KOSPI 주식 종목 종가                    | `/v3/market/closed/kospi/{issuecode}/closeprice`                            |
| 주식     | 주식실시간종가A       | KOSPI지수                           | `/v3/market/closed/kospi/index`                                             |
| 주식     | 주식실시간종가A       | KOSPI 주식 공매도 일별조회                 | `/v3/market/closed/kospi/{issucode}/shortsell`                              |
| 주식     | 주식실시간종가A       | KOSPI 주식 외국인 보유율 히스토리             | `/v3/market/closed/kospi/{issucode}/foreignhistory`                         |
| 주식     | 주식실시간종가A       | KOSPI 주식 종목 히스토리                  | `/v3/market/closed/kospi/{issuecode}/history`                               |
| 주식     | 주식실시간종가B       | KOSDAQ 주식 종목 리스트                  | `/v3/market/closed/kosdaq/lists`                                            |
| 주식     | 주식실시간종가B       | &#xD;KOSDAQ 주식 종목 마스터             | `/v3/market/closed/kosdaq/{issuecode}/master`                               |
| 주식     | 주식실시간종가B       | KOSDAQ 주식 종목 마스터 (요구형)            | `/v3/market/closed/kosdaq/{issuecode}/selectivemaster`                      |
| 주식     | 주식실시간종가B       | KOSDAQ 주식 종목 종가                   | `/v3/market/closed/kosdaq/{issuecode}/closeprice`                           |
| 주식     | 주식실시간종가B       | KOSDAQ 지수                         | `/v3/market/closed/kosdaq/index`                                            |
| 주식     | 주식실시간종가B       | KOSDAQ 주식 공매도 일별조회                | `/v3/market/closed/kosdaq/{issucode}/shortsell`                             |
| 주식     | 주식실시간종가B       | KOSDAQ 주식 외국인 보유율 히스토리            | `/v3/market/closed/kosdaq/{issucode}/foreignhistory`                        |
| 주식     | 주식실시간종가B       | KOSDAQ 주식 종목 히스토리                 | `/v3/market/closed/kosdaq/{issuecode}/history`                              |
| 주식     | 주식실시간종가C       | 주식종목(ETF) 장마감후 순자산가치              | `/v3/market/closed/etf/{marketcode}/{issuecode}/closenav`                   |
| 주식     | 주식실시간A         | (시세표)KOSPI 주식 현재가 리스트             | `/v3/market/realtime/kospi/multiquote/stocks/lists`                         |
| 주식     | 주식실시간A         | (시세표)KOSPI 주식 시고저종 리스트            | `/v3/market/realtime/kospi/multiquote/stocks/ohlclists`                     |
| 주식     | 주식실시간A         | (시세표)KOSPI 주식 시장별 시간외단일가 시고저종 리스트 | `/v3/market/realtime/kospi/multiquote/stocks/ahtohlclists`                  |
| 주식     | 주식실시간A         | (시세표)KOSPI 주식 호가/잔량 리스트           | `/v3/market/realtime/kospi/multiquote/stocks/quotelists`                    |
| 주식     | 주식실시간A         | (시세표)KOSPI 주식 복수종목 현재가            | `/v3/market/realtime/kospi/multiquote/stocks/price`                         |
| 주식     | 주식실시간A         | (시세표)KOSPI 주식 복수종목 호가잔량           | `/v3/market/realtime/kospi/multiquote/stocks/orderbook`                     |
| 주식     | 주식실시간A         | KOSPI 주식 종목 체결                    | `/v3/market/realtime/kospi/stocks/{issuecode}/price`                        |
| 주식     | 주식실시간A         | KOSPI 주식 종목 호가잔량(LP호가제외)          | `/v3/market/realtime/kospi/stocks/{issuecode}/orderbook`                    |
| 주식     | 주식실시간A         | KOSPI 주식 종목 일중                    | `/v3/market/realtime/kospi/stocks/{issuecode}/intraday`                     |
| 주식     | 주식실시간A         | KOSPI 주식 거래상위 회원사 정보              | `/v3/market/realtime/kospi/stocks/{issuecode}/traderanking`                 |
| 주식     | 주식실시간B         | (시세표)KOSDAQ주식 현재가 리스트             | `/v3/market/realtime/kosdaq/multiquote/stocks/lists`                        |
| 주식     | 주식실시간B         | (시세표)KOSDAQ주식 시고저종 리스트            | `/v3/market/realtime/kosdaq/multiquote/stocks/ohlclists`                    |
| 주식     | 주식실시간B         | (시세표)KOSDAQ주식시간외단일가 시고저종 리스트      | `/v3/market/realtime/kosdaq/multiquote/stocks/ahtohlclists`                 |
| 주식     | 주식실시간B         | (시세표)KOSDAQ주식 호가/잔량 리스트           | `/v3/market/realtime/kosdaq/multiquote/stocks/quotelists`                   |
| 주식     | 주식실시간B         | (시세표)KOSDAQ주식 복수종목 현재가            | `/v3/market/realtime/kosdaq/multiquote/stocks/price`                        |
| 주식     | 주식실시간B         | (시세표)KOSDAQ주식 복수종목 호가잔량           | `/v3/market/realtime/kosdaq/multiquote/stocks/orderbook`                    |
| 주식     | 주식실시간B         | KOSDAQ주식 종목 체결                    | `/v3/market/realtime/kosdaq/{issuecode}/price`                              |
| 주식     | 주식실시간B         | KOSDAQ주식 종목 호가잔량(LP호가제외)          | `/v3/market/realtime/kosdaq/{issuecode}/orderbook`                          |
| 주식     | 주식실시간B         | KOSDAQ주식 종목 일중                    | `/v3/market/realtime/kosdaq/{issuecode}/intraday`                           |
| 주식     | 주식실시간B         | KOSDAQ주식 거래상위 회원사 정보              | `/v3/market/realtime/kosdaq/{issuecode}/traderanking`                       |
| 기타     | 유가종목별투자자       | KOSPI 주식 종목별 투자자별 매매동향 (종가)       | `/v3/market/investors/kospi/{issucode}/investors`                           |
| 기타     | 유가종목별투자자       | KOSPI지수 투자자 마감정보                  | `/v3/market/investors/kospi/investors`                                      |
| 기타     | 코스닥종목별투자자      | KOSDAQ주식 종목별 투자자별 매매동향 (종가)       | `/v3/market/investors/kosdaq/{issuecode}/investors`                         |
| 기타     | 코스닥종목별투자자      | KOSDAQ지수 투자자 마감정보                 | `/v3/market/investors/kosdaq/investors`                                     |
| 기타     | 부가서비스          | KOSPI ETF 구성종목 정보                 | `/v3/market/extra/stocks/kospi/{issuecode}/pdf`                             |
| 기타     | 부가서비스          | KOSDAQ ETF 구성종목 정보                | `/v3/market/extra/stocks/kosdaq/{issuecode}/pdf`                            |
| 기타     | 부가서비스          | KOSPI ETF 종목 nav 조회               | `/v3/market/extra/stocks/kospi/{issuecode}/nav`                             |
| 기타     | 부가서비스          | KOSDAQ ETF 종목 nav 조회              | `/v3/market/extra/stocks/kosdaq/{issuecode}/nav`                            |
| 기타     | 부가서비스          | KOSPI ETF 종목 nav 히스토리             | `/v3/market/extra/stocks/kospi/{issuecode}/navhistory`                      |
| 기타     | 부가서비스          | KOSDAQ ETF 종목 nav 히스토리            | `/v3/market/extra/stocks/kosdaq/{issuecode}/navhistory`                     |
| 기타     | 부가서비스          | 국가별 휴장일 정보                        | `/v3/market/extra/stocks/{nationcode}/holiday`                              |
| 파생     | 파생실시간종가A       | 상품/지수 선물 종목 리스트                   | `/v3/market/closed/derivative/futures/{marketcode}/lists`                   |
| 파생     | 파생실시간종가A       | 상품/지수 선물 종목 마스터                   | `/v3/market/closed/derivative/futures/{marketcode}/l{issucode}/master`      |
| 파생     | 파생실시간종가A       | 상품/지수 선물 종목 종가                    | `/v3/market/closed/derivative/futures/{marketcode}/{issucode}/closeprice`   |
| 파생     | 파생실시간종가A       | 상품/지수 선물 종목 히스토리                  | `/v3/market/closed/derivative/futures/{marketcode}/{issucode}/history`      |
| 파생     | 파생실시간종가A       | 상품/지수 옵션 종목 리스트                   | `/v3/market/closed/derivative/options/{marketcode}/lists`                   |
| 파생     | 파생실시간종가A       | 상품/지수 옵션 종목 마스터                   | `/v3/market/closed/derivative/options/{marketcode}/{issucode}/master`       |
| 파생     | 파생실시간종가A       | 상품/지수 옵션 종목 종가                    | `/v3/market/closed/derivative/options/{marketcode}/{issucode}/closeprice`   |
| 파생     | 파생실시간종가A       | 상품/지수 옵션 종목 히스토리                  | `/v3/market/closed/derivative/options/{marketcode}/{issucode}/history`      |
| 파생     | 파생실시간A         | 상품/지수 선물\_체결                      | `/v3/market/realtime/derivative/futures/{marketcode}/{issuecode}/price`     |
| 파생     | 파생실시간A         | 상품/지수 선물\_우선호가                    | `/v3/market/realtime/derivative/futures/{marketcode}/{issuecode}/orderbook` |
| 파생     | 파생실시간A         | 상품/지수 선물 투자자별 매매동향                | `/v3/market/realtime/derivative/futures/{marketcode}/market/investors`      |
| 파생     | 파생실시간A         | 상품/지수 선물 일중                       | `/v3/market/realtime/derivative/futures/{marketcode}/{issuecode}/intraday`  |
| 파생     | 파생실시간A         | 상품/지수 옵션\_체결                      | `/v3/market/realtime/derivative/options/{marketcode}/{issuecode}/price`     |
| 파생     | 파생실시간A         | 상품/지수 옵션\_우선호가                    | `/v3/market/realtime/derivative/options/{marketcode}/{issuecode}/oederbook` |
| 파생     | 파생실시간A         | 상품/지수 옵션 투자자별 매매동향                | `/v3/market/realtime/derivative/options/{marketcode}/market/investors`      |
| 파생     | 파생실시간A         | 상품/지수 옵션 일중                       | `/v3/market/realtime/derivative/options/{marketcode}/{issuecode}/intraday`  |
| 업종     | KRX업종실시간종가     | 업종 종가                             | `/v3/market/closed/index/{marketcode}/{issuecode}/closeindex`               |
| 업종     | KRX업종실시간종가     | 업종 히스토리                           | `/v3/market/closed/index/{marketcode}/{issuecode}/history`                  |
| 업종     | KRX업종 실시간      | 업종 시가총액                           | `/v3/market/realtime/index/{marketcode}/{issucode}/marketcap`               |
| 업종     | KRX업종 실시간      | 업종 예상지수                           | `/v3/market/realtime/index/{marketcode}/{issucode}/prospectindex`           |
| 업종     | KRX업종 실시간      | 업종 일중                             | `/v3/market/realtime/index/{marketcode}/{issucode}/intraday`                |
| 업종     | KRX업종 실시간      | 업종 지수                             | `/v3/market/realtime/index/{marketcode}/{issucode}/index`                   |
| 업종     | KRX업종 실시간      | 업종 투자자별 매매동향                      | `/v3/market/realtime/index/{marketcode}/{issucode}/investors`               |



##





