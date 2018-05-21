---
description: 시세 서비스 개요
---

# 개요

## Open API 시세 정보

 다양한 금융시장정보의 실시간 및  과거데이타를 이용하기 편한 **Restful API** 및 **WebSocket** 서비스로 제공



## 제공 데이터

### A.  조회 서비스

#### 종가정보 조회  

장개시전 및 장마감정보에 대한 조회

> PRESET  
>  : 주식종목마스터와 같이 조회시 지정된 58개 항목 전체가 결과값으로 보여줌
>
> 요구형  
>  : 주식종목마스터 제공항목 및 추가항목 \('19.1.1 기준, 총 75개항목\) 중    
>    필요한 항목만 선택조합하여 조회 가능 \(요구형항목 참조\)



#### 실시간시세 조회

실시간 가격정보, 장개시전 및 장마감정보에 대한 조회

> PRESET     
>  : 주식종목체결과 같이 조회시 지정된 14개 항목 전체가 결과값으로 보여줌
>
> 요구형  
>  : 추후 제공 예정





### B.  스트리밍 서비스

#### WebSocket 종목별 상세 구독

> PRESET     
> : 체결 및 호가데이타를 4개 항목그룹\(tick, quote, tick10, quote10\)으로 묶어서 시세 발생시 수신
>
> 요구형 \(change\)  
>  : 실시간 전송가능 한 모든 항목 중에서 필요한 항목만 선택조합하여 시세 발생시 수신

세션당 200개의 실시간 구독 가능  
     ex\) 200종목에 대한 체결데이타만 구독  또는 100종목에 대한 체결 및 호가데이타 구독



#### WebSocket 시장별 체결 구독

1개 세션에 유가/코스닥/선물/옵션기준으로 전종목의 요약 체결정보\(종목코드, 체결가, 체결량, 시간\) 전송

{% page-ref page="undefined-4.md" %}

{% hint style="success" %}
고객요청에 따라 당사의 풍부한 데이타를  다양한 방식으로 제공가능 
{% endhint %}







## 송수신 프로토콜



### A. 전문 프로토콜

#### OPEN API 데이타 프로토콜

     GET 방식 조회서비스               \|   JSON-RPC 2.0

     Web Socket 실시간 서비스     \|   JSON-RPC 2.0 



#### JSON-RPC 2.0

     JSON-RPC 2.0 주요 Object member

> `jsonrpc`           \|    버전  
> `method`            \|    업무구분  
> `params`             \|    업무구분에 대한 데이타  
> `id`                      \|     id, key  
> `result`             \|    요청에 대한 응답  
> `error`               \|    에러처리 \("code", "mesage" member를 가짐\)

     송수신 전문 

> 요청 \(Request\)           \|  실시간 구독  요청/취소 및 조회요청 \(method:~, params : ~  \)   
>                                           \*  method 값 구분   
>                                               "`init`" : Websocket 초기화,  "`subscribe`" : 구독,    
>                                               "`unsubscribe`" :구독해제,  "`query`" :  조회요청  
> 응답 \(Response\)        \|  실시간 구독  요청/취소 및 조회요청 \(result :  ~ \)  
> 통보 \(Notification \)    \|  실시간 시세 데이타 \(method : push, params :  ~ \) , id 를 보내지 않는다.  
> 에러 \(Error\)                 \|  요청에 대한 에러 \(error:  ~  \)

[www.jsonrpc.org/specification](http://www.jsonrpc.org/specification) 참조

실시간 시세 전송은 Notification 으로 처리 \("method":"push" 이고,  "id" member는 없음\)

URI 기반 조회 요청 시 RPC 2.0 데이타 구조의 예외 허용   
\(조회요청 데이타 "method", "id" member 누락 허용\)





### B. 조회업무 관련 송수신전문

  1. 조회요청  
     시장/종목별  요구형/Preset 데이타 조회 요청

  2. 조회응답  
     조회 요청에 대한 정상응답 \( result : ~\)

  3. 에러  
     조회 요청에 대한 에러응답  \( error : ~\)  
     조회요청에  대해 조회결과 또는 에러를 반드시 전송한다.  
     일중/일별 과거 데이타 조회는 최대 100건까지 가능함





### C. 실시간업무 관련 송수신전문

  1. 초기화   
     업무개시를 위한 세션정보 전송 요청 \(method: init, ~ \)

  2. 구독요청    
     시장/종목별 요구형/PRESET 실시간 데이타를  요청 \(method:subscribe, ~ \)

  3. 구독취소   
     실시간 데이타 요청을 취소 \(method:unsubscribe, ~ \)

  4. 구독응답    
     구독요청/취소에 대한 정상응답 \(result:~ \)

  5. 에러  
     구독요청/구독취소에 대한 에러응답 \(error:~\)

  6. 실시간   
     실시간 데이타 발생시 전송되는 시세데이타 \(method:push, ~ \)

  7. 채널점검    
     Heartbeat 점검 \(method:heartbeat, ~\)

실시간 구독요청시 실시간구독항목이 아닌 데이타를 구독요청하면 에러를 전송한다.  

세션당 200개의 실시간 구독 가능  
ex\) 200종목에 대한 체결데이타만 구독  또는 100종목에 대한 체결 및 호가데이타 구독\)





### D. 실시간 업무흐름

####  WebSocket 종목별 상세 구독

1. 실시간 데이타 수신을 위해 WebSocket  Session연결
2. 업무개시를 위한 세션정보 전송 요청 \(`method`: init,  `data` : API key, 회사명 \)
3. 연결된 Session을 통해서 종목 기준으로 업무요건별로 Subscribe/Unsubscribe  요청을 한다.
4. 구독요청 결과에 대해서  Push시세\(현재 시세메모리 정보\)  또는 에러를 반드시 전송한다.
5. 구독하는 종목에 대한 시세 발생시 비동기 방식으로 실시간 데이타 전송
6. WebSocket Session 종료시 모든 실시간 구독내역은 초기화 된다.

![WebSocket &#xC885;&#xBAA9;&#xBCC4; &#xC0C1;&#xC138; &#xAD6C;&#xB3C5;](../.gitbook/assets/image%20%2830%29.png)

#### WebSocket  시장별 체결구독

1. 실시간 데이타 수신을 위해 WebSocket  Session연결
2. 업무개시를 위한 세션정보 전송 요청 \(`method`: init,  `data` :API key, 회사명 \)
3. 업무개시 이후 발생되는 체결데이타부터 별도 절차 없이 시장기준으로 전송됨

   \(여러 종목을 배열형태로 전송\)

4. WebSocket Session 종료

\*  세션 연결 전에 조회서비스를 통해서 전종목 시세 수신을 권장합니다.

![WebSocket  &#xC2DC;&#xC7A5;&#xBCC4; &#xCCB4;&#xACB0;&#xAD6C;&#xB3C5;](../.gitbook/assets/image%20%2826%29.png)





### E. 송수신전문 예

####   1. 요청 \(Request\)

   1-1. GET 방식 조회

![GET &#xC870;&#xD68C;](../.gitbook/assets/image%20%2811%29.png)

   1-2. WebSocket 초기화

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

   1-3. WebSocket 실시간 구독요청/취소

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

   1-4. WebSocket 채널점검 \(Heartbeat\)

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



####   2. 응답 \(Response\)

```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "result"  {
        "message" : "ok"
    }
}

{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "result" :  {
        "isuSrtCd": "005930",
        "trdPrc":1310000,  
        "trdvol":86,
        "trdTm":09450155,
        "mkStatTpCd":1
    }
}
```



####   3. 통보 \(Notification\)

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

####   4. 에러 {#3-notification}

```yaml
{
    "jsonrpc" : "2.0"
    "error" :  {
        "message" :  "정상적인 JSON-RPC 형식이 아닙니다",
        "code" : 47
    }
}
```



