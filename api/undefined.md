# 주문 서비스

### 국제 표준전문인 FIX 기반의 주문 처리

* 표준화된 API제공으로 증권사별로 별도의 개발이 불필요
* KRX에 특화된 전문 개발 불필요 \(유연한 사업모델 창출 가능\)

### 신속한 개발 가능

* 로보어드바이저 및  핀테크 기업에 기술 친화적인 Restful 방식의 API 제공
* FIX 주문처리를 위한 별도의 FIX Engine 개발 부담 감소

### STP-HUB 이용

* STP-HUB를 이용함에 따라 증권사의 추가 개발 부담 최소화
* 여러 증권사에 동시에 직접 주문이 가능 하므로 확장성이 좋음

{% hint style="info" %}
### [STP-HUB](https://www.koscom.co.kr/portal/main/contents.do?menuNo=200451) \(Straight Through Processing HUB\)

 국내외 여러 자산운용사가 국내 여러 증권사에 동시에 직접 주문을 가능하게 해주는 허브 시스템으로, 증권사를 통한 주문에서 결제까지의 전과정 자동화를 지원합니다.
{% endhint %}

### 주문 서비스 구조

![](../.gitbook/assets/image%20%2853%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>① - 신규주문 (New Order Single), 신규주문(New Order List – 현 사용 불가), 주문 정정(Order
          Cancel/Replace Request), 주문 취소(Order Cancel Request), 리스트 주문 취소 (List Cancel
          Request) 용 Restful API 호출</p>
        <p>- 주문응답 수신을 위한 subscription 전송하여 web socket session을 설정</p>
        <p>② Restful API 요청의 Body에 포함된 주문전문(JSON)을 FIX 메시지 형태로 변환하여 STP-HUB로 전송 ③
          오픈플랫폼은 API 요청에 대한 응답을 즉시 전송 - JSON message 수준에서의 기본적인 오류를 확인하여 응답</p>
        <p>④ ~ ⑦ 주문전문은 STP-HUB를 거쳐 증권사 및 거래소로 전달되고, 그 응답을 역순으로 반환</p>
        <p>⑧ 응답 (Execution Reports), 거부 (Order Cancel Reject) FIX 메시지를 JSON으로 변환하여
          자문사와 연결된 WebSocket Session을 통해 전송</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>{% hint style="info" %}
#### 자세한 설명은  [자본시장 공동 핀테크 오픈 플랫폼 주문 API](https://developers.koscom.co.kr/resources/documentation/FIX_REST_API_v1.03.pdf) 을 참조 하세요.
{% endhint %}



