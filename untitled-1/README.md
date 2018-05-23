---
description: 코스콤 시세API 요약
---

# D. 시세서비스

## URI

| **`구분`** | **Name** | **`URI`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| WS | 종목별 실시간상세 \(유가+코스닥\) | /ws |
| WS | 유가증권 전종목실시간 | /ws\_ksp |
| WS | 코스닥 전종목실시간 | /ws\_kdq |
| 시세 | 주식시장별 현재가리스트 | /v2/market/multiquote/stocks/{marketcode}/lists |
| 시세표 | 주식시장별 시고저 현재가리스트 | /v2/market/multiquote/stocks/{marketcode}/ohlclists |
| 시세표 | 주식 복수종목 현재가 | /v2/market/multiquote/stocks/{marketcode}/price |
| 시세표 | 주식 복수종목 호가잔량 | /v2/market/multiquote/stocks/{marketcode}/orderbook |
| 주식 | 주식 종목 리스트 | /v2/market/stocks/{marketcode}/lists |
| 주식 | 주식 종목 마스터 | /v2/market/stocks/{marketcode}/{issuecode}/master |
| 주식 | 주식 종목 마스터\(요구형\) | /v2/market/stocks/{marketcode}/{issuecode}/selectivemaster |
| ~~주식~~ | ~~주식 실시간\(요구형\)~~ | ~~/v2/market/stocks/{marketcode}/{issuecode}/selectivereal~~ |
| 주식 | 주식 종목 종가 | /v2/market/stocks/{marketcode}/{issuecode}/closeprice |
| 주식 | 주식 종목 체결 | /v2/market/stocks/{marketcode}/{issuecode}/price |
| 주식 | 주식 종목 호가잔량\(LP호가제외\) | /v2/market/stocks/{marketcode}/{issuecode}/orderbook |
| 주식 | 주식 종목별 투자자별 종가 | /v2/market/stocks/{marketcode}/{issuecode}/investors |
| 주식 | KOSPI/KOSDAQ지수 투자자 마감정보 | /v2/market/stocks/{marketcode}/investors |
| 주식 | KOSPI/KOSDAQ지수 | /v2/market/stocks/{marketcode}/index |
| 주식 | 주식종목\(ETF\) 장마감후 순자산가치 | /v2/market/stocks/{marketcode}/{issuecode}/closenav |
| 주식 | 주식 공매도 일별조회 | /v2/market/stocks/{marketcode}/{issuecode}/shortsell |
| 주식 | 주식 종목 일중 | /v2/market/stocks/{marketcode}/{issuecode}/intraday |
| 주식 | 주식 거래상위 회원사 정보 | /v2/market/stocks/{marketcode}/{issuecode}/traderaking |
| 주식 | 주식 외국인 보유율 히스토리 | /v2/market/stocks/{marketcode}/{issuecode}/foreignhistory |
| 주식 | 주식 종목 히스토리 | /v2/market/stocks/{marketcode}/{issuecode}/history |
| 선 | 상품/지수선물 종목 리스트 | /v2/market/futures/{marketcode}/lists |
| 선물 | 상품/지수선물 종목 마스터 | /v2/market/futures/{marketcode}/{issuecode}/master |
| 선물 | 상품/지수선물 종목 종가 | /v2/market/futures/{marketcode}/{issuecode}/closeprice |
| 선물 | 상품/지수선물\_체결 | /v2/market/futures/{marketcode}/{issuecode}/price |
| 선물 | 상품/지수선물\_우선호가 | /v2/market/futures/{marketcode}/{issuecode}/orderbook |
| 선물 | 상품/지수선물 일중 | /v2/market/futures/{marketcode}/{issuecode}/intraday |
| 선물 | 상품/지수선물 종목 히스토리 | /v2/market/futures/{marketcode}/{issuecode}/history |
| 옵션 | 상품/지수 옵션 종목 리스트 | /v2/market/options/{marketcode}/lists |
| 옵션 | 상품/지수 옵션 종목 마스터 | /v2/market/options/{marketcode}/{issuecode}/master |
| 옵션 | 상품/지수옵션 종목 종가 | /v2/market/options/{marketcode}/{issuecode}/closeprice |
| 옵션 | 상품/지수옵션\_체결 | /v2/market/options/{marketcode}/{issuecode}/price |
| 옵션 | 상품/지수옵션\_우선호가 | /v2/market/options/{marketcode}/{issuecode}/orderbook |
| 옵션 | 상품/지수옵션 일중 | /v2/market/options/{marketcode}/{issuecode}/intraday |
| 옵션 | 상품/지수옵션 종목 히스토리 | /v2/market/options/{marketcode}/{issuecode}/history |
| 업종 | 업종 종가 | /v2/market/index/{marketcode}/{issuecode}/closeindex |
| 업종 | 업종 지수 | /v2/market/index/{marketcode}/{issuecode}/index |
| 업종 | 업종 예상지수 | /v2/market/index/{marketcode}/{issuecode}/prospectindex |
| 업종 | 업종 시가총액 | /v2/market/index/{marketcode}/{issuecode}/marketcap |
| 업종 | 업종 투자자별 | /v2/market/index/{marketcode}/{issuecode}/investors |
| 업종 | 업종 일중 | /v2/market/index/{marketcode}/{issuecode}/intraday |
| 업종 | 업종 히스토리 | /v2/market/index/{marketcode}/{issuecode}/history |

{% hint style="info" %}
고객업무 요청시 협의 후 추가 API 제공가능
{% endhint %}



## 설명 

| **Name** | **Time** | **Description** | **License** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 종목별 실시간상세 \(유가+코스닥\) | 실시간 | 선택종목\(호가+체결:100종목/200종목\)에 대한 상세 체결/호가 | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용라이선스 |
| 유가증권 전종목실시간 | 실시간 | 유가증권 시장 전종목 단순 체결\(체결가, 체결량, 시간\)  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용라이선스 |
| 코스닥 전종목실시간 | 실시간 | 코스닥 시장 전종목 단순 체결\(체결가, 체결량, 시간\)  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용라이선스 |
| 주식시장별 현재가리스트 | 실시간 | 시장별 전종목 스냅샷 시세\(현재가 기준, 데이타생성주기 1초\) | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용라이선스 |
| 주식시장별 시고저 현재가리스트 | 실시간 | 시장별 전종목 스냅샷 시세\(시가,고가,저가,현재가, 데이타생성주기 1초\) | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용라이선스 |
| 주식 복수종목 현재가 | 실시간 | 복수종목\(최대 20종목\)에 대한 실시간 현재가 조회  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용라이선스 |
| 주식 복수종목 호가잔량 | 실시간 | 복수종목\(최대 20종목\)에 대한 실시간 호가잔량 조회  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용라이선스 |
| 주식 종목 리스트 | 6:30 | 종목리스트 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 주식 종목 마스터 | 6:30 | 종목배치 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 주식 종목 마스터\(요구형\) | 6:30 | 종목배치-종목별 고객이 요구하는 항목만 조회 결과로 전송함 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| ~~주식 실시간\(요구형\)~~ | ~~실시간~~ | \* 개발 예정\(3.0\) | ~~실시간\(증권ABC선택\)~~ |
| 주식 종목 종가 | 전일,당일 15:40이후 | 종목 당일 종가제공 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 주식 종목 체결 | 실시간 | 종목\_체결 | 실시간\(증권ABC선택\) |
| 주식 종목 호가잔량\(LP호가제외\) | 실시간 | 종목\_호가잔량\_LP호가\_제외 | 실시간\(증권ABC선택\) |
| 주식 종목별 투자자별 종가 | 전일,당일 15:30이후 | 종목별투자자별 종가 | 종가정보\(종목별투자자\) |
| KOSPI/KOSDAQ지수 투자자 마감정보 | 전일,당일 15:40이후 | KOSPI/KOSDAQ 투자자 마감정보\(업종-투자자별 참고\) | 종가정보\(종목별투자자\) |
| KOSPI/KOSDAQ지수 | 실시간 | KOSPI/KOSDAQ 실시간 지수 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 주식종목\(ETF\) 장마감후 순자산가치 | 전일,당일 16:00이후 | ETF 종목에 대한 NAV \(해외ETF종목 Nav는 환율/기초자산 변동시 조회시점에 따라 다른값이 조회됨\) | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 주식 공매도 일별조회 | 전일,당일 18:00이후 | 18시 이후 제공 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 주식 종목 일중 | 실시간 | 종목 일중 데이터 제공 \(10초, 1분, 10분단위 시/고/저/종\) | 실시간\(증권ABC선택\) |
| 주식 거래상위 회원사 정보 | 실시간 | 종목 매수/매도 상위 5개 회원사 정보 | 실시간\(증권ABC선택\) |
| 주식 외국인 보유율 히스토리 | 6:30 | 종목 외국인 보유율 과거 데이터 제공 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 주식 종목 히스토리 | 6:30 | 종목 일별 과거 데이터 제공 | 종가정보\(증권ABC선택\), 실시간\(증권ABC선택\) |
| 상품/지수선물 종목 리스트 | 6:30 | 종목리스트 | 종가정보\(파생상품A\), 실시간\(파생\) |
| 상품/지수선물 종목 마스터 | 6:30 | 선물 종목에 대한 기초 자료 제공 | 종가정보\(파생상품A\), 실시간\(파생\) |
| 상품/지수선물 종목 종가 | 15:50 | 선물 당일 종가제공 | 종가정보\(파생상품A\), 실시간\(파생\) |
| 상품/지수선물\_체결 | 실시간 | 데이터 발생시마다 실시간 제공 | 실시간\(파생상품A\) |
| 상품/지수선물\_우선호가 | 실시간 | 데이터 발생시마다 실시간 제공 | 실시간\(파생상품A\) |
| 상품/지수선물 일중 | 실시간 | 상품/지수선물 일중 데이터 제공 \(10초, 1분, 10분단위 시/고/저/종\) | 실시간\(증권ABC선택\) |
| 상품/지수선물 종목 히스토리 | 6:30 | 상품/지수선물 종목 일별 과거데이터 제공\(연결선물코드표 참\) | 종가정보\(파생상품A\), 실시간\(파생\) |
| 상품/지수 옵션 종목 리스트 | 6:30 | 종목리스트 | 종가정보\(파생상품A\), 실시간\(파생\) |
| 상품/지수 옵션 종목 마스터 | 6:30 | 옵션 종목에 대한 기초 자료 제공 | 종가정보\(파생상품A\), 실시간\(파생\) |
| 상품/지수옵션 종목 종가 | 전일,당일 15:50이후 | 옵션 당일 종가제공 | 종가정보\(파생상품A\), 실시간\(파생\) |
| 상품/지수옵션\_체결 | 실시간 | 데이터 발생시마다 실시간 제공 | 실시간\(파생상품A\) |
| 상품/지수옵션\_우선호가 | 실시간 | 데이터 발생시마다 실시간 제공 | 실시간\(파생상품A\) |
| 상품/지수옵션 일중 | 실시간 | 상품/지수옵션 데이터 제공 \(10초, 1분, 10분단위 시/고/저/종\) | 실시간\(증권ABC선택\) |
| 상품/지수옵션 종목 히스토리 | 6:30 | 상품/지수옵션 종목 일별 과거 데이터 제공 | 종가정보\(파생상품A\), 실시간\(파생\) |
| 업종 종가 | 전일,당일 15:40이후 | 업종 당일 종가제공 | 종가정보\(KRX지수\), 실시간\(KRX지수\) |
| 업종 지수 | 실시간 | 전체 업종지수\(KOSPI/KOSDAQ지수 포함\) | 실시간\(KRX지수\) |
| 업종 예상지수 | 실시간 | 전체 업종예상지수\(KOSPI/KOSDAQ지수 포함\) | 실시간\(KRX지수\) |
| 업종 시가총액 | 실시간 | 전체 업종시가총액\(KOSPI/KOSDAQ지수 포함\) | 실시간\(KRX지수\) |
| 업종 투자자별 | 실시간 | 전체 업종 투자자별\(KOSPI/KOSDAQ지수 포함\) | 실시간\(KRX지수\) |
| 업종 일중 | 실시간 | 전체 업종 일중 데이터 제공 \(10초, 1분, 10분단위 시/고/저/종\) | 실시간\(증권ABC선택\) |
| 업종 히스토리 | 6:30 | 전체 업종 일별 과거 데이터 제공\(KOSPI/KOSDAQ지수 포함\) | 종가정보\(KRX지수\), 실시간\(KRX지수\) |



