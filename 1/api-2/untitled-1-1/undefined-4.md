---
description: 실시간 스트리밍 시세 (WebSocket 방식)
---

# 스트리밍

유가증권시장\(코스피, 코스닥\) 및 파생상품\(선물시장,옵션시장\)의 호가 및 체결 정보를 실시간으로 제공한다.



### **주요 특징**

* Web Socket 을 통해서 실시간 송수신 지원
* 시장데이타 발생 시 미리 정의된 체결, 호가 데이타구조의 데이타가 일괄적으로 전송
* tick, quote 는 tick10, quote10 의 단축형으로 모든 시장에 대해 동일하게 전송 가능
* tick10, quote10 은 주식/선물/옵션시장별 체결, 호가조회 데이타와 동일
* 아래는 주식기준으로 기술하였으며, 시장별 일부 데이타 항목만 상이함
* 유가증권, 코스닥 전종목 시세 제공
* **종목 호가 및 체결**은 **1세션**, 동시 **최대 200건**으로 제한,  샌드박스 : 1세션 최대 20건으로 제한



## 1. 실시간 시세

WebSocket 세션연결후 개별 종목기준으로 실시간 데이타 수신등록\(subscribe\)하면, 등록된 종목의 시세 변동시 지정된 항목등 \(preset 방식\) 또는 요청한 항목들 \(요구형- change\) 이 실시간으로 전송\(publish\) 됨 

**Summary**            \|   **session 연결 후 subscribe & publish**

세션기준 200건 등록\(subscribe\) 가능 - 체결, 호가 동시 등록시 100종목



{% api-method method="head" host="ws://sandbox-apigw.koscom.co.kr:9887" path="/ws/" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}





## 2. 전종목 실시간 시세

WebSocket 세션을 연결하면, 시장기준 전종목의 현재가가 변경시 주기적\(0.5 초 이내\)으로 종목코드, 시간, 체결가, 누적거래량을 전송

**Summary**            \|   **session 연결 후 publish without subscribe**  
데이타 항목        \|   종목코드, 체결가, 체결수량, 시간

데이타 전송의 효율성을 위하여 최대 50건씩 Packing 하여 전송  
별도의 데이터 복구 및 재전송 작업 없음

{% hint style="warning" %}
 장 시간 중에만 실시간 데이터 발생
{% endhint %}



## Syntax

Methods               \|   **Web Socket**

Authentication     \|   **API Key**



{% api-method method="options" host="ws://sandbox-apigw.koscom.co.kr" path="/{ws\_marketcode}/" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="ws\_marketcode" type="string" required=true %}
 kospi 또는 kosdaq \(ex. ws\_ksp \| ws\_kdq \)
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
[
    {
        "isuSrtCd" : "000210",
        "trdPrc" : "81000",
        "trdVol" : "5", 
        "trdTm" : "14340400"
    },
    {    
        "isuSrtCd" : "500032",
        "trdPrc" : "12760",
        "trdVol" : "400", 
        "trdTm" : "14340400"
    },
    ...이하 생략...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Send Msg \(init 전문송신\)

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



