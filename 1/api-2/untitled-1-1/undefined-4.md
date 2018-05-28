---
description: 실시간 스트리밍 시세 (WebSocket 방식)
---

# 스트리밍

유가증권시장\(코스피, 코스닥\) 및 파생상품\(선물시장,옵션시장\)의 호가 및 체결 정보를 실시간으로 제공한다.

{% hint style="danger" %}
문의; 실시간 Guide는 상세한 설명제공 안하는 거 같았음 :O
{% endhint %}

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

#### 

#### WebSocket Address

```text
ws://sandbox-apigw.koscom.co.kr/블라블라/ws
```

#### 

#### Request Example - Preset Type

```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "method"  : "subscribe" ,
    "params" :  {
        "preset" : "tick",
        "isuSrtCd" : "005930"
    }
}
```

#### Request Example - Change Type

```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "method"  : "subscribe" ,
    "params" :  {
        "preset" : "change",
        "isuSrtCd" : "005930",
        "items" : ["trdPrc", "trdTm"]
    }
}
```

#### Request Example - UnSubscribe

```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "method"  : "unsubscribe" ,
    "params" :  {
        "preset" : "quote" ,
        "isuSrtCd" : "005930"
        }
}
```

#### 

#### Response Msg Example - OK

```yaml
{
    "jsonrpc" : "2.0",
    "id" : 1 ,
    "result"  {
        "message" : "ok"
    }
}
```

#### Response Msg Example - Error

```yaml
{
    "jsonrpc" : "2.0"
    "error" :  {
        "message" :  "정상적인 JSON-RPC 형식이 아닙니다",
        "code" : 47
    }
}
```



#### Response Date Example - Preset Type

```yaml
{
    "jsonrpc":"2.0",
    "method":"push",
    "params":{
        "preset":"quote",
        "isuSrtCd":"005930",
        "askStep1BstordPrc":2465000,
        "askStep1BstordRqty":144,
        "bidStep1BstordPrc":2464000,
        "bidStep1BstordRqty":298
    }
}
{
    "jsonrpc":"2.0",
    "method":"push",
    "params":{
        "preset":"tick",
        "isuSrtCd":"005930",
        "trdPrc":2465000,
        "trdvol":2,
        "accTrdvol":251916,
        "accTrdval":627899637000,
        "trdTm":14412000
    }
}
```

#### Response Data Example - Change Type

```text

```













## 2. 전종목 실시간 시세

WebSocket 세션을 연결하면, 시장기준 전종목의 현재가가 변경시 주기적\(0.5 초 이내\)으로 종목코드, 시간, 체결가, 누적거래량을 전송

**Summary**            \|   **session 연결 후 publish without subscribe**  
데이타 항목        \|   종목코드, 체결가, 체결수량, 시간

데이타 전송의 효율성을 위하여 최대 50건씩 Packing 하여 전송  
별도의 데이터 복구 및 재전송 작업 없음  
채널점검용 heartbeat 송수신 가능

{% hint style="warning" %}
 장 시간 중에만 실시간 데이터 발생
{% endhint %}

#### 

#### WebSocket Address

```text
ws://sandbox-apigw.koscom.co.kr/블라블라/{ws_marketcode}
```

> `ws_marketcode`   :  kospi 또는 kosdaq \(ex. ws\_ksp \| ws\_kdq \)

#### 

#### Request Example - Init 전문 송신

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

#### 

#### Response Example

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







## Preset 데이터 항목구성

### tick

> 체결

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| trdPrc | Number\(11\) | 체결가격 |  |
| trdvol | Number\(10\) | 체결수량,거래량 |  |
| trdTm | String\(8\) | 체결시각,거래시각 | \*테이블 하단 참고 |

> `trdTm`  
> HHMMSSmm 형태로 시간전송  
>    - 정규장 개시전 또는 정규장 체결 발생 이전 : 0  
>    - 장운영시그널, 대량체결 포함  
> ※ _장운영시그널_  
> 정규장마감\(15:00\):31000000 /장종료시간외마감\(15:30\):41000000 /단일가마감\(18:00\):81000000 /일반Buy-in마감\(18:00\):91000007 /당일Buy-in마감\(18:00\):91000008  
> ※ _대량체결시_   
> 장전대량매매체결:51000000 /장중대량매매체결:61000000 /장후대량매매체결:71000000



### quote

> 호가

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | String\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| accTrdvol | Number\(12\) | 누적체결수량,누적거래량 | 단위: 주 |
| askStep1BstordPrc | Number\(11\) | 매도1단계우선호가가격 |  |
| bidStep1BstordPrc | Number\(11\) | 매수1단계우선호가가격 |  |
| askStep1BstordRqty | Number\(12\) | 매도1단계우선호가잔량 |  |
| bidStep1BstordRqty | Number\(12\) | 매수1단계우선호가잔량 |  |



### quote10

> 10호가

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 -&gt; 00660 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위: 주 |
| askStep1BstordPrc | number\(11\) | 매도1단계우선호가가격 |  |
| bidStep1BstordPrc | number\(11\) | 매수1단계우선호가가격 |  |
| askStep1BstordRqty | number\(12\) | 매도1단계우선호가잔량 |  |
| bidStep1BstordRqty | number\(12\) | 매1단계우선호가잔량 |  |
| askStep2BstordPrc | number\(11\) | 매도2단계우선호가가격 |  |
| bidStep2BstordPrc | number\(11\) | 매수2단계우선호가가격 |  |
| askStep2BstordRqty | number\(12\) | 매도2단계우선호가잔량 |  |
| bidStep2BstordRqty | number\(12\) | 매수2단계우선호가잔량 |  |
| askStep3BstordPrc | number\(11\) | 매도3단계우선호가가격 |  |
| bidStep3BstordPrc | number\(11\) | 매수3단계우선호가가격 |  |
| askStep3BstordRqty | number\(12\) | 매도3단계우선호가잔량 |  |
| bidStep3BstordRqty | number\(12\) | 매수3단계우선호가잔량 |  |
| askStep4BstordPrc | number\(11\) | 매도4단계우선호가가격 |  |
| bidStep4BstordPrc | number\(11\) | 매수4단계우선호가가격 |  |
| askStep4BstordRqty | number\(12\) | 매도4단계우선호가잔량 |  |
| bidStep4BstordRqty | number\(12\) | 매수4단계우선호가잔량 |  |
| askStep5BstordPrc | number\(11\) | 매도5단계우선호가가격 |  |
| bidStep5BstordPrc | number\(11\) | 매수5단계우선호가가격 |  |
| askStep5BstordRqty | number\(12\) | 매도5단계우선호가잔량 |  |
| bidStep5BstordRqty | number\(12\) | 매수5단계우선호가잔량 |  |
| askStep6BstordPrc | number\(11\) | 매도6단계우선호가가격 |  |
| bidStep6BstordPrc | number\(11\) | 매수6단계우선호가가격 |  |
| askStep6BstordRqty | number\(12\) | 매도6단계우선호가잔량 |  |
| bidStep6BstordRqty | number\(12\) | 매수6단계우선호가잔량 |  |
| askStep7BstordPrc | number\(11\) | 매도7단계우선호가가격 |  |
| bidStep7BstordPrc | number\(11\) | 매수7단계우선호가가격 |  |
| askStep7BstordRqty | number\(12\) | 매도7단계우선호가잔량 |  |
| bidStep7BstordRqty | number\(12\) | 매수7단계우선호가잔량 |  |
| askStep8BstordPrc | number\(11\) | 매도8단계우선호가가격 |  |
| bidStep8BstordPrc | number\(11\) | 매수8단계우선호가가격 |  |
| askStep8BstordRqty | number\(12\) | 매도8단계우선호가잔량 |  |
| bidStep8BstordRqty | number\(12\) | 매수8단계우선호가잔량 |  |
| askStep9BstordPrc | number\(11\) | 매도9단계우선호가가격 |  |
| bidStep9BstordPrc | number\(11\) | 매수9단계우선호가가격 |  |
| askStep9BstordRqty | number\(12\) | 매도9단계우선호가잔량 |  |
| bidStep9BstordRqty | number\(12\) | 매수9단계우선호가잔량 |  |
| askStep10BstordPrc | number\(11\) | 매도10단계우선호가가격 |  |
| bidStep10BstordPrc | number\(11\) | 매수10단계우선호가가격 |  |
| askStep10BstordRqty | number\(12\) | 매도10단계우선호가잔량 |  |
| bidStep10BstordRqty | number\(12\) | 매수10단계우선호가잔량 |  |
| askordTotRqty | number\(12\) | 매도호가총잔량 |  |
| bidordTotRqty | number\(12\) | 매수호가총잔량 |  |
| pstoffhrAskTotOrdRqty | number\(15\) | 장종료후시간외매도총호가잔량 |  |
| pstoffhrBidTotOrdRqty | number\(15\) | 장종료후시간외매수총호가잔량 |  |
| deemTrdPrc | number\(11\) | 예상체결가격 |  |
| deemTrdvol | number\(12\) | 예상체결수량 |  |
| deemAccTrdvol | number\(12\) | 예상누적체결수량 |  |



### tick10

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 |
| cmpprevddTpCd | string\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 단위:원 / 신주인수권 증서&증권의 신규 상장 당일 : 0 |
| opnprc | number\(11\) | 시가 | 단위:원 |
| hgprc | number\(11\) | 고가 | 단위:원 |
| lwprc | number\(11\) | 저가 | 단위:원 |
| trdPrc | number\(11\) | 체결가격 | 0 |
| trdvol | number\(10\) | 체결수량, 거래량 | 0 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |
| lstAskbidTpCd | string\(1\) | 최종매도매수구분코드 | 1:매도, 2:매수 \(최종으로 들어온 호가의 매도매수구분값\) |
| trdTm | string\(8\) | 체결시각,거래시각 | \*테이블 하단 참고 |
| askordPrc\_1 | number\(11\) | 매도호가가격\_1 | 단위:원 \(체결+우선호가 발생시에만 전송\) |
| bidordPrc\_1 | number\(11\) | 매수호가가격\_1 |  단위:원 |

> `trdTm`  
> HHMMSSmm 형태로 시간전송  
>    - 정규장 개시전 또는 정규장 체결 발생 이전 : 0  
>    - 장운영시그널, 대량체결 포함  
> ※ _장운영시그널_  
> 정규장마감\(15:00\):31000000 /장종료시간외마감\(15:30\):41000000 /단일가마감\(18:00\):81000000 /일반Buy-in마감\(18:00\):91000007 /당일Buy-in마감\(18:00\):91000008  
> ※ _대량체결시_   
> 장전대량매매체결:51000000 /장중대량매매체결:61000000 /장후대량매매체결:71000000



### index

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
| isuSrtCd | String\(3\) | 업종코드 | 코드표 &gt; 업종 참조 |
| trdTm | String\(8\) | 체결시각,거래시각 | \*테이블 하단 참고 |
| trdPrc | number\(10\) | 지수 |  |
| cmpprevddTpCd | String\(1\) | 전일대비구분코드 | 1:상한/2:상승/3:보합/4:하한/5:하락/6:기세상한/7:기세상승/8:기세하한/9:기세하락 |
| cmpprevddPrc | number\(11\) | 전일대비지수 |  |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 단위:주 |
| accTrdval | number\(22\) | 누적거래대금 | 단위:원 |

> `trdTm`  
> "HHMMSSmm" 형태로 시간전송  
>    - 정규장 개시전 또는 정규장 체결 발생 이전 : 0  
>    - 장운영시그널, 대량체결 포함  
> _※ 장운영시그널_  
> 정규장마감\(15:00\):31000000 /장종료시간외마감\(15:30\):41000000 /단일가마감\(18:00\):81000000 /일반Buy-in마감\(18:00\):91000007 /당일Buy-in마감\(18:00\):91000008  
> _※ 대량체결시_   
> 장전대량매매체결:51000000/장중대량매매체결:61000000/장후대량매매체결:71000000"



