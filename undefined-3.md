# 개정내역

## REST API Developer Guide  변경이력

| **`버전`** | **`개정일`** | **`개정내역`** | **`비고`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `0.91` | 16.07.26 | Request 요청 중 불필요한 필드 삭제 외 3건 |  |
| `0.92` | 16.07.27 | OAuth 인증 Type API 호출 시 header에 apikey 삽입 정책 삭제 |  |
| `1.0` | 17.05.30 | API 제공유형 추가 외 3건 |  |
| `1.01` | 17.06.26 | Complex -&gt; Object, Complex Array -&gt; Array | 문자 변경 |
| `1.02` | 17.07.11 | 주문체결조회 전문의 “qrAccNo”선택 -&gt; 필수 | Required 변경 |
| `1.03` | 17.08.01 | 금융투자 핀테크 포털 수정 및 오핀 모바일 앱 추가  |  |
| `1.04` | 17.08.17 | 일임매매 page 항목 String변경\(24=&gt;100\) | p80 ~ 106 |
| **`1.05`** | **17.08.22** | 일임 계좌잔고 조회 balance 항목 제거 외 1건 | p88, p94 |



## 시세 서비스  변경이력

| **`버전`** | **`개정내역`** | **`가동일`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| `1.0` | 시세 Guide 신규 작성 |  |
| `2.0` | 정보 OPEN API 재구축 \(주식조회, 실시간 시세 제공\) | 16.06.01 |
| `2.1` | 정보 OPEN API 가동 \(주식/선물/옵션/업종조회 - 20개API, 실시간 시세제공 - 1개\) | 16.09.01 |
| `2.2` | 주식 : 주식종목 마스터 항목추가\(결산월, 결산월구분, 수정주가산출여부\) / 업종 : KOSPI,KOSDAQ 시가총액 조회추가 | 17.01.31 |
| `2.3` | \*\[수정\] 선물,옵션종목 마스터 API에서 전일대비 구분코드\(cmpprevddTpCd\) 삭제      \*\[신규\] 전체시장 종가 API 신규추가 / 주식 KOSPI,KOSDAQ지수 종가 신규추가 / 주식 KOSPI,KOSDAQ지수 투자자별 종가 신규추가 | 17.03.24 |
| `2.4` | \*\[수정-항목명 변경\] 조회\(업종\) - 업종예상지수 : 필드명변경\(pro-&gt;deem\)     \*\[수정\] 조회\(주식\) - 주식종목마스터 : 전일순자산가치\(NAV\)추가 / 조회\(주식\) - 주식종목호가잔량 : 예상누적체결수량 추가 / 실시간\(Preset\) - quote10 : 예상누적체결수량 추가 / 실시간\(요구형\) - 주식 : 예상누적체결수량 추가      \*\[신규\] 일중데이타조회 추가 \(10,60,600초 기준 조회\) / 조회\(주식\) - 주식종목일중 / 조회\(업종\) - 주식종목일중 /조회\(선물\) - 주식종목일중 / 조회\(옵션\) - 주식종목일중 | 17.06.30 |
| `2.41` | \*\[신규\] 조회\(주식\) - 주식종목 장마감이후 순자산 가치\(NAV\)     \*\[신규\] 실시간채널\(WebSocket\)에 heartbeat 추가\(method:heartbeat\) | 17.07.28 \[17.07.20 18:00 이후\] |
| `2.42` | \*\[신규\] 조회\(주식\) - 주식공매도/대차      \*\[수정-업무변경\] 조회\(주식\) -KOSPI,KOSDAQ 지수종가 ==&gt; KOSPI,KOSDAQ 지수 \(/v2/market/stocks/{marketcode}/closeindex ==&gt; index\)    \*\[수정-시장추가\] 조회\(선물\) : KOSDAQ150선물시장 추가  \*\[수정-코드추가\] 조회\(선물\) :연결선물코드 추가 | 17.11.03 18:00 이후 |
| `2.5` | \*\[신규\] 조회\(주식\) - 주식종목마스터\(요구형\) : 필요한 항목만 조합하여 조회,공매도과열지정일, 과거 평균 가격/거래량 정보 추가     \*\[수정-항목추가\] 조회\(주식\) - 주식 공매도 : 공매도거래금액, 대차거래금액 추가     \*\[수성-항목삭제\] 조회\(주식\) - 주식 종목 마스터 : 주식업종대분류코드, 주식업종소분류코드 \(대표지수외 구성종목여부 구분 삭제\)     \*\[수정-문서변경\] 개요 및 프로토콜 Tab 내용 변경, 요구형항목Tab 생성 | 17.12.08 18:00 이후 |
| `2.52` | \*\[신규\] 시세표 - 주식 실시간 현재가 리스트 | 17.12.15 18:00 이후 |
| `2.6` | \*\[신규\] WS - 유가증권 전종목실시간시세 / WS - 코스닥 전종목실시간시세 |  |
| `2.7` | \*\[신규\] 시세표 - 복수종목현재가조회 / 시세표 - 복수종목호가잔량조회\(예정\) | 18.02.16 18:00 이후 |
| `2.8` | \*\[신규\] 조회\(주식\) - 주식 거래상위 회원사 정보 / 조회\(주식\) - 주식 외국인 보유율 히스토리      \*\[항목추가\] 요구형항목\(조회\) - 영업일\(BzDd\) | 18.03.30 18:00 이후 |
| **`2.81`** | \*\[신규\] 시세표 - 주식시장별 시고저 현재가 리스트 | **18.04.28** 18:00 이후 |



## OFin SDK 가이드 변경이력

| **`버전`** | **`개정일`** | **`개정내역`** | **`비고`** |
| --- | --- | --- |
| **`android v1.0`** | **2017.06.22** | 초안 작성 |  |
| **`ios v1.0`** | **2017.06.22** | 초안 작성 |  |



