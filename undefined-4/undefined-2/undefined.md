---
description: 핀테크 서비스 애플리케이션 등록
---

# 애플리케이션 등록

대시보드 &gt; 어플리케이션 에서 하단에 있는 '**응용 프로그램 추가'** 버튼을 통해 앱을 생성 합니다.

![](../../.gitbook/assets/image%20%28104%29.png)

​



## Application 정보 등록

'Application 정보'에 해당 항목을 입력하고 'Next Step' 버튼을 클릭 합니다.

![](../../.gitbook/assets/image%20%2855%29.png)

> * 응용 프로그램 이름
> * 플랫폼
>
>        서비스 플랫폼 유형 및 참고정보이며 이 값에 따라 제공되는 API 특성이 결정되지는 않습니다.
>
> * 설명



## API 관리 정보 등록

'API관리' 탭에서는 사용할 API를 선택하고, 그에 해당하는 API '이용 약관에 동의' 하고, 더 이상 사용할 API가 없으면 'Next Step'버튼을 누릅니다.

![](../../.gitbook/assets/image%20%2899%29.png)

> * API 추가 
>
>        Subscribing을 원하는 API를 선택
>
> * 이용약관 동의



## 인증 정보 등록

![&#xC778;&#xC99D; &#xD0ED;](../../.gitbook/assets/image%20%28100%29.png)

{% hint style="danger" %}
인증 탭의 '**Callback URL**',  **'Scope**',  '**유형**' 항목은   
사용할 API의 인증 방식이 **OAuth** \(현재는 OAuth2.0만 지원\)일 때는 **필수로 입력**해야 합니다.  
Scope 항목은 [이곳](https://koscom.gitbook.io/open-api/api-1/oauth/scope) 에서 확인하세요.
{% endhint %}

{% hint style="warning" %}
'API문서&gt;서비스' Swagger UI로 OAuth2.0 테스트 할 경우   
Callback URL에 아래와 같이 입력하세요 : [https://developers.koscom.co.kr/resources/oauthCallback.html](https://developers.koscom.co.kr/resources/oauthCallback.html)
{% endhint %}

유형은 'public' 를 선택 합니다. \(현재는 OAuth2.0 Grant Type 중 Authorization Code 방식만 지원함\)  
'저장' 버튼을 누르고 정상적으로 접수가 되면 앱이 추가 되고, 앱 상태가 '승인 보류'가 됩니다.

![&#xC571; &#xC2B9;&#xC778;&#xBCF4;&#xB958;](../../.gitbook/assets/image%20%281%29.png)

개발자센터 관리자가 해당 앱의 사용을 승인하면 회원정보에 등록된 이메일로 '앱 승인' 메일을 받으실 수 있습니다. 앱 등록 정책에 맞지 않으면 해당 사유와 함께 거부 될 수도 있습니다.



