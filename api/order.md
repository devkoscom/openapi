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

![](../.gitbook/assets/image%20%2858%29.png)

<table>
  <thead>
    <tr>
      <th style="text-align:left">
        <p>&#x2460; - &#xC2E0;&#xADDC;&#xC8FC;&#xBB38; (New Order Single), &#xC2E0;&#xADDC;&#xC8FC;&#xBB38;(New
          Order List &#x2013; &#xD604; &#xC0AC;&#xC6A9; &#xBD88;&#xAC00;), &#xC8FC;&#xBB38;
          &#xC815;&#xC815;(Order Cancel/Replace Request), &#xC8FC;&#xBB38; &#xCDE8;&#xC18C;(Order
          Cancel Request), &#xB9AC;&#xC2A4;&#xD2B8; &#xC8FC;&#xBB38; &#xCDE8;&#xC18C;
          (List Cancel Request) &#xC6A9; Restful API &#xD638;&#xCD9C;</p>
        <p>- &#xC8FC;&#xBB38;&#xC751;&#xB2F5; &#xC218;&#xC2E0;&#xC744; &#xC704;&#xD55C;
          subscription &#xC804;&#xC1A1;&#xD558;&#xC5EC; web socket session&#xC744;
          &#xC124;&#xC815;</p>
        <p>&#x2461; Restful API &#xC694;&#xCCAD;&#xC758; Body&#xC5D0; &#xD3EC;&#xD568;&#xB41C;
          &#xC8FC;&#xBB38;&#xC804;&#xBB38;(JSON)&#xC744; FIX &#xBA54;&#xC2DC;&#xC9C0;
          &#xD615;&#xD0DC;&#xB85C; &#xBCC0;&#xD658;&#xD558;&#xC5EC; STP-HUB&#xB85C;
          &#xC804;&#xC1A1;</p>
        <p>&#x2462; &#xC624;&#xD508;&#xD50C;&#xB7AB;&#xD3FC;&#xC740; API &#xC694;&#xCCAD;&#xC5D0;
          &#xB300;&#xD55C; &#xC751;&#xB2F5;&#xC744; &#xC989;&#xC2DC; &#xC804;&#xC1A1;
          - JSON message &#xC218;&#xC900;&#xC5D0;&#xC11C;&#xC758; &#xAE30;&#xBCF8;&#xC801;&#xC778;
          &#xC624;&#xB958;&#xB97C; &#xD655;&#xC778;&#xD558;&#xC5EC; &#xC751;&#xB2F5;</p>
        <p>&#x2463; ~ &#x2466; &#xC8FC;&#xBB38;&#xC804;&#xBB38;&#xC740; STP-HUB&#xB97C;
          &#xAC70;&#xCCD0; &#xC99D;&#xAD8C;&#xC0AC; &#xBC0F; &#xAC70;&#xB798;&#xC18C;&#xB85C;
          &#xC804;&#xB2EC;&#xB418;&#xACE0;, &#xADF8; &#xC751;&#xB2F5;&#xC744; &#xC5ED;&#xC21C;&#xC73C;&#xB85C;
          &#xBC18;&#xD658;</p>
        <p>&#x2467; &#xC751;&#xB2F5; (Execution Reports), &#xAC70;&#xBD80; (Order
          Cancel Reject) FIX &#xBA54;&#xC2DC;&#xC9C0;&#xB97C; JSON&#xC73C;&#xB85C;
          &#xBCC0;&#xD658;&#xD558;&#xC5EC; &#xC790;&#xBB38;&#xC0AC;&#xC640; &#xC5F0;&#xACB0;&#xB41C;
          WebSocket Session&#xC744; &#xD1B5;&#xD574; &#xC804;&#xC1A1;</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>{% hint style="info" %}
#### 자세한 설명은  [자본시장 공동 핀테크 오픈 플랫폼 주문 API](https://developers.koscom.co.kr/resources/documentation/FIX_REST_API_v1.03.pdf) 을 참조 하세요.
{% endhint %}



