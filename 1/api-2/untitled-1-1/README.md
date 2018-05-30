---
description: 코스콤(정보사업부) 제공
---

# 시세 서비스

## Open API 시세 정보

 다양한 금융시장정보의 실시간 및  과거데이터를 이용하기 편한 **Restful API** 및 **WebSocket** 서비스로 제공



## API  URI

| **`구분`** | **Name** | **`URI`** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| WS | 종목별 실시간상세 \(유가+코스닥\) | /ws |
| WS | 유가증권 전종목실시간 | /ws\_ksp |
| WS | 코스닥 전종목실시간 | /ws\_kdq |
| 시세표 | 주식시장별 현재가리스트 | /v2/market/multiquote/stocks/{marketcode}/lists |
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
| 선물 | 상품/지수선물 종목 리스트 | /v2/market/futures/{marketcode}/lists |
| 선물 | 상품/지수선물 종목 마스터 | /v2/market/futures/{marketcode}/{issuecode}/master |
| 선물 | 상품/지수선물 종목 종가 | /v2/market/futures/{marketcode}/{issuecode}/closeprice |
| 선물 | 상품/지수선물\_체결 | /v2/market/futures/{marketcode}/{issuecode}/price |
| 선물 | 상품/지수선물\_우선호가 | /v2/market/futures/{marketcode}/{issuecode}/orderbook |
| 선물 | 상품/지수선물 일중 | /v2/market/futures/{marketcode}/{issuecode}/intraday |
| 선물 | 상품/지수선물 종목 히스토리 | /v2/market/futures/{marketcode}/{issuecode}/history |
| 옵션 | 상품/지수 옵션 종목 리스트 | /v2/market/options/{marketcode}/lists |
| 옵션 | 상품/지수 옵션 종목 마스터 | /v2/market/options/{marketcode}/{issuecode}/master |
| 옵션 | 상품/지수 옵션 종목 종가 | /v2/market/options/{marketcode}/{issuecode}/closeprice |
| 옵션 | 상품/지수 옵션\_체결 | /v2/market/options/{marketcode}/{issuecode}/price |
| 옵션 | 상품/지수 옵션\_우선호가 | /v2/market/options/{marketcode}/{issuecode}/orderbook |
| 옵션 | 상품/지수 옵션 일중 | /v2/market/options/{marketcode}/{issuecode}/intraday |
| 옵션 | 상품/지수 옵션 종목 히스토리 | /v2/market/options/{marketcode}/{issuecode}/history |
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



## API  Summary

| **Name** | **Time** | **Description** | **License** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 종목별 실시간상세 \(유가+코스닥\) | 실시간 | 선택종목\(호가+체결:100종목/200종목\)에 대한 상세 체결/호가 | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용 라이선스 |
| 유가증권 전종목실시간 | 실시간 | 유가증권 시장 전종목 단순 체결\(체결가, 체결량, 시간\)  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용 라이선스 |
| 코스닥 전종목실시간 | 실시간 | 코스닥 시장 전종목 단순 체결\(체결가, 체결량, 시간\)  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API세션사용 라이선스 |
| 주식시장별 현재가리스트 | 실시간 | 시장별 전종목 스냅샷 시세\(현재가 기준, 데이타생성주기 1초\) | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API 시세표사용 라이선스 |
| 주식시장별 시고저 현재가리스트 | 실시간 | 시장별 전종목 스냅샷 시세\(시가,고가,저가,현재가, 데이타생성주기 1초\) | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API 시세표사용 라이선스 |
| 주식 복수종목 현재가 | 실시간 | 복수종목\(최대 20종목\)에 대한 실시간 현재가 조회  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API 시세표사용 라이선스 |
| 주식 복수종목 호가잔량 | 실시간 | 복수종목\(최대 20종목\)에 대한 실시간 호가잔량 조회  | 실시간\(증권A/B/C,파생A,KRX지수 선택\) + API 시세표사용 라이선스 |
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





## 제공 데이터

### 조회 서비스 \(Restful API\)

**종가정보 조회     \|**    장개시전 및 장마감정보에 대한 조회

| **PRESET** | 주식종목마스터와 같이 조회시 지정된 58개 항목 전체가 결과값으로 보여줌 |
| --- | --- |
| **요구형 \(change\)** | 주식종목마스터 제공항목 및 추가항목\('19.1.1 기준, 총 75개항목\) 중 필요한 항목만 선택조합하여 조회 가능 \([요구형항목](https://koscom.gitbook.io/open-api/1/api-2/untitled-1-1/undefined-1) 참조\) |

  
**실시간시세 조회   \|**    실시간 가격정보, 장개시전 및 장마감정보에 대한 조회

| **PRESET** | 주식종목체결과 같이 조회시 지정된 14개 항목 전체가 결과값으로 보여줌 |
| --- | --- |
| **요구형 \(change\)** | 추후 제공 예정 |

  
조회\(시세\) API는 아래 페이지에서 참조하세요 **:** 

{% page-ref page="undefined-9/" %}



### 스트리밍 서비스 \(WebSocket\)

**종목별 상세 구독**

세션당 200개의 실시간 구독 가능  
    ex\) 200종목에 대한 체결데이타만 구독  또는 100종목에 대한 체결 및 호가데이타 구독

| **PRESET** | 체결 및 호가데이타를 4개 항목그룹\(tick, quote, tick10, quote10\)으로 묶어서 시세 발생시 수신 |
| --- | --- |
| **요구형 \(change\)** | 실시간 전송가능 한 모든 항목 중에서 필요한 항목만 선택조합하여 시세 발생시 수신  |

  
**시장별 체결 구독**

1개 세션에 유가/코스닥/선물/옵션기준으로 전종목의 요약 체결정보\(종목코드, 체결가, 체결량, 시간\) 전송

  
스트리밍\(시세\) API는 아래 페이지에서 참조하세요 **:** 

{% page-ref page="undefined-4.md" %}

{% hint style="success" %}
고객요청에 따라 당사의 풍부한 데이타를  다양한 방식으로 제공가능 
{% endhint %}



## 송수신 프로토콜



### A. 전문 프로토콜

**OPEN API 데이타 프로토콜**

GET 방식 조회서비스                \|   `JSON-RPC 2.0`

Web Socket 실시간 서비스      \|   `JSON-RPC 2.0`



**JSON-RPC 2.0**

JSON-RPC 2.0 주요 Object member

| `jsonrpc` | 버전 |
| --- | --- | --- | --- | --- | --- |
| `method` | 업무구분 |
| `params` | 업무구분에 대한 데이타 |
| `id` | id, key |
| `result` | 요청에 대한 응답 |
| `error` | 에러처리 \("code", "mesage" member를 가짐\) |

  
송수신 전문 

| **요청** \(Request\)  | 실시간 구독 요청/취소 및 조회요청 | method : ~ /  param : ~ |
| --- | --- | --- | --- |
| **응답** \(Response\) | 실시간 구독  요청/취소 및 조회요청 | result : ~ |
| **통보** \(Notification\) | 실시간 시세 데이타 \(id를 보내지 않는다\) | method : push / params : ~  |
| **에러** \(Error\)  | 요청에 대한 에러 | error:  ~ |

> 요청\(Request\)  method 값 구분  
>    **:**   "init" : Websocket 초기화,  "subscribe" : 구독,  "unsubscribe" : 구독해제,  "query" :  조회요청

실시간시세 전송은 Notification으로 처리 \("method":"push" 이고,  "id" member는 없음\)  
URI 기반 조회 요청 시 RPC 2.0 데이타 구조의 예외 허용 \(조회요청 데이타 "method", "id" member 누락 허용\)

{% hint style="info" %}
JSON-RPC 2.0 에 관한 자세한 설명은[ 이곳](http://www.jsonrpc.org/specification)을 참조하세요.
{% endhint %}





### B. 조회업무 관련 송수신전문

| **조회요청** \(Request\) | 시장/종목별  요구형/Preset  데이타 조회 요청 |  |
| --- | --- | --- |
| **조회응답** \(Response\) | 조회 요청에 대한 정상응답  | result : ~ |
| **에러** \(Error\) | 조회 요청에 대한 에러응답 | error : ~ |

조회요청에 대해 조회결과 또는 에러를 반드시 전송한다.   
일중/일별 과거 데이타 조회는 최대 100건까지 가능함





### C. 실시간업무 관련 송수신전문

| **초기화** | 업무개시를 위한 세션정보 전송 요청 | method: init, ~ |
| --- | --- | --- | --- | --- | --- | --- |
| **구독요청** | 시장/종목별 요구형/PRESET 실시간 데이타를  요청 | method:subscribe, ~  |
| **구독취소** | 실시간 데이타 요청을 취소 | method:unsubscribe, ~  |
| **구독응답** | 구독요청/취소에 대한 정상응답 | result:~ |
| **에러** | 구독요청/구독취소에 대한 에러응답 | error:~ |
| **실시간** | 실시간 데이타 발생시 전송되는 시세데이타 | method:push, ~ |
| **채널점검** | Heartbeat 점검 | method:heartbeat, ~ |

실시간 구독요청시 실시간구독항목이 아닌 데이타를 구독요청하면 에러를 전송한다.  

세션당 200개의 실시간 구독 가능  
  ex\) 200종목에 대한 체결데이타만 구독  또는 100종목에 대한 체결 및 호가데이타 구독\)





### D. 실시간 업무흐름

####  WebSocket 종목별 상세 구독

1. 실시간 데이타 수신을 위해 WebSocket  Session 연결
2. 업무개시를 위한 세션정보 전송 요청 \(`method`: init,  `data` : API key, 회사명 \)
3. 연결된 Session을 통해서 종목 기준으로 업무요건별로 Subscribe/Unsubscribe  요청을 한다.
4. 구독요청 결과에 대해서  Push시세\(현재 시세메모리 정보\)  또는 에러를 반드시 전송한다.
5. 구독하는 종목에 대한 시세 발생시 비동기 방식으로 실시간 데이타 전송
6. WebSocket Session 종료 시 모든 실시간 구독내역은 초기화 된다.

![WebSocket &#xC885;&#xBAA9;&#xBCC4; &#xC0C1;&#xC138; &#xAD6C;&#xB3C5;](../../../.gitbook/assets/image%20%2877%29.png)

#### WebSocket  시장별 체결구독

1. 실시간 데이타 수신을 위해 WebSocket  Session 연결
2. 업무개시를 위한 세션정보 전송 요청 \(`method`: init,  `data` :API key, 회사명 \)
3. 업무개시 이후 발생되는 체결데이타부터 별도 절차 없이 시장기준으로 전송됨

   \(여러 종목을 배열형태로 전송\)

4. WebSocket Session 종료

![WebSocket &#xC2DC;&#xC7A5;&#xBCC4; &#xCCB4;&#xACB0;&#xAD6C;&#xB3C5;](../../../.gitbook/assets/image%20%282%29.png)

{% hint style="success" %}
세션 연결 전에 조회서비스를 통해서 전종목 시세 수신을 권장합니다.
{% endhint %}





### E. 송수신전문 예

#### 요청 \(Request\)

 1. GET 방식 조회

![](../../../.gitbook/assets/image%20%2827%29.png)

 2. WebSocket 초기화

{% code-tabs %}
{% code-tabs-item title="init" %}
```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1,
    "method"  : "init",
    "params" :  {
        "key" : "XXXXXXXX" ,
        "membername" : "XXX Company"
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 3. WebSocket 실시간 구독요청/취소

{% code-tabs %}
{% code-tabs-item title="subscribe" %}
```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1,
    "method"  : "subscribe",
    "params" :  {
        "preset" : "quote" ,
        "isuSrtCd" : "005930"
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

 4. WebSocket 채널점검 \(Heartbeat\)

{% code-tabs %}
{% code-tabs-item title="heartbeat" %}
```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1,
    "method"  : "heartbeat",
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}



#### 응답 \(Response\)

```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "result" : {
        "message" : "ok"
    }
}

{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "result" : {
        "isuSrtCd": "005930",
        "trdPrc":1310000,  
        "trdvol":86,
        "trdTm":09450155,
        "mkStatTpCd":1
    }
}
```



####  통보 \(Notification\)

```yaml
{
    "jsonrpc" : "2.0",
    "method"  : "push"
    "params" : {
        "preset" : "tick"
        "isuSrtCd" : 005930,
        "trdPrc" : 1310000,  
        "trdvol" : 86,
        "trdTm" : 09450155
    }
}
```

####  {#3-notification}

#### 에러 \(Error\) {#3-notification}

```yaml
{
    "jsonrpc" : "2.0"
    "error" :  {
        "message" :  "정상적인 JSON-RPC 형식이 아닙니다",
        "code" : 47
    }
}
```



