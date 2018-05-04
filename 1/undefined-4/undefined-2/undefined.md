---
description: 핀테크 서비스 애플리케이션 등록
---

# 애플리케이션 등록

대시보드 &gt; 어플리케이션 에서 하단에 있는 ‘응용 프로그램 추가’ 버튼을 통해 앱을 생성 합니다.

## Application 정보 등록

![Application &#xC815;&#xBCF4;](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9n-1MugBfAycrCN1bv%2F-LAHJcYwaH-5GNazBe7P%2F-LAHKn-mQ2ZQaG3TKWHb%2Fimage.png?alt=media&token=2a89deef-d775-4013-8663-188b01fad47f)

> * 응용 프로그램 이름
> * 플랫폼 
>   * 서비스 플랫폼 유형이며, 참고정보이며 이 값에 따라 제공되는 API 특성이 결정되지는 않습니다.
> * 설명

‘Application 정보’에 해당 항목을 입력하고, ‘Next Step’ 버튼을 클릭 합니다.

## API 관리 정보 등록

![API &#xAD00;&#xB9AC;](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9n-1MugBfAycrCN1bv%2F-LAHLMIksCiDl7fXXKe7%2F-LAHLRxbARYHiDNX-4Vt%2Fimage.png?alt=media&token=a494c308-4362-4f43-87c9-c5d2f1da8657)

> * API 추가 
>   * Subscribing을 원하는 API를 선택
> * 이용약관 동의

‘API관리’ 탭에서는 사용할 API를 선택하고, 그에 해당하는 API ‘이용 약관에 동의’ 하고, 더 이상 사용할 API가 없으면 ‘Next Step’버튼을 누릅니다.

## 인증 정보 등록

![&#xC778;&#xC99D;](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9n-1MugBfAycrCN1bv%2F-LAHLMIksCiDl7fXXKe7%2F-LAHLwSpVrDTTzAgWrN4%2Fimage.png?alt=media&token=6d522aff-9363-4812-9769-1817ad5a7040)

> * Callback URL
> * Scope
> * 유형

{% hint style="warning" %}
인증 탭의 _Callback URL_, _Scope_, _유형_ 항목은   
사용할 API의 인증 방식이 OAuth \(현재는 OAuth2.0만 지원\)일 때는 **필수**로 입력해야 합니다.
{% endhint %}

유형은 ‘public’ 를 선택 합니다. \(현재는 OAuth2.0 Grant Type 중 Authorization Code 방식만 지원함\)

 ‘API문서 &gt; 서비스’의 Swagger UI로 OAuth2.0을 테스트 하시려면, Callback URL을 아래와 같이 입력하세요. [https://developers.koscom.co.kr/resources/oauthCallback.html](https://developers.koscom.co.kr/resources/oauthCallback.html)

‘저장’ 버튼을 누르고 정상적으로 접수가 되면 앱이 추가 되고, 앱 상태가 ‘승인 보류’가 됩니다.

![&#xC571; &#xC2B9;&#xC778;&#xBCF4;&#xB958;](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9n-1MugBfAycrCN1bv%2F-LAHMd1O9_k5lmk0MyGD%2F-LAHMjLHKHa0dLf-OqQJ%2Fimage.png?alt=media&token=0a4ce3c3-daab-4b1b-9b68-36aa2b7a20b7)

 개발자센터 관리자가 해당 앱의 사용을 승인하면 회원정보에 등록된 이메일로 ‘앱 승인’ 메일을 받으실 수 있습니다. 앱 등록 정책에 맞지 않으면 해당 사유와 함께 거부 될 수도 있습니다. 

