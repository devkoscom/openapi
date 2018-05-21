---
description: API 테스트절차
---

# API 테스트

본 페이지에서는 **API Key** 및 **OAuth2.0** 인증에 관한 **테스트절차**를 다룹니다.   
'APIs & 플랜’ 메뉴에서 테스트 하려는 API의 인증유형을 확인합니다.

![APIs &#xBA54;&#xB274;](../../../.gitbook/assets/image%20%286%29.png)

인증방식에 대한 자세한 설명을 원하실 경우, [이곳](https://koscom.gitbook.io/open-api/~/edit/primary/1/api-1)을 참조하세요.



## API Key 인증방식

‘API문서 &gt; 시세 서비스 &gt; 주식종목’ 메뉴에서 ‘Select an Application’ 을 눌러서 앱을 선택 합니다.  
앱이 보이지 않으시면 해당 API를 사용하는 앱을 먼저 만드셔야 합니다. 자세한 사항은 [이곳](https://koscom.gitbook.io/open-api/1/undefined-4/undefined-2/undefined#application)을 참조하세요.

![&#xC2DC;&#xC138;&#xC11C;&#xBE44;&#xC2A4; - &#xC8FC;&#xC2DD;&#xC885;&#xBAA9;](../../../.gitbook/assets/image%20%2870%29.png)

‘Authentication \(None\)’ 버튼을 __누르시고, 인증방식을 ‘API Key’로 선택 합니다.

![&#xC778;&#xC99D;&#xBC29;&#xC2DD; &#xC120;&#xD0DD;](../../../.gitbook/assets/image%20%2824%29.png)

해당 API의 Method가 GET방식이면 ‘API Key Type’를 Query로 선택 하시고, POST방식이면 Header로 선택 하세요.

![&#xC778;&#xC99D;&#xBC29;&#xC2DD; - API Key](../../../.gitbook/assets/image%20%2851%29.png)

테스트할 API를 선택 하시고, ‘Try it Out’ 버튼을 누르시면 아래와 같이 Response 결과를 받아 보실 수 있습니다.

![Response &#xACB0;&#xACFC;](../../../.gitbook/assets/image%20%2880%29.png)

 ‘Query’ 탭을 누르시면 Request 및 다양한 개발언어별 샘플코드를 참고 하실 수 있습니다.

![Query &#xD0ED;](../../../.gitbook/assets/image%20%2818%29.png)



## OAuth 인증방식

{% hint style="warning" %}
현재는 OAuth2.0 Grant Type 중 **Authorization Code만 지원**하며, Implicit Grant Type 등은 보안수준 및 비즈니스모델에 따라 협의가 필요합니다. 
{% endhint %}

![&#xC571; &#xC120;&#xD0DD;](../../../.gitbook/assets/image%20%288%29.png)

‘APIs & 플랜’ 메뉴에서 ‘OAuth2.0-Authorization Code를 지원하는 API를 확인 합니다. 테스트할 앱을 선택하고, ‘OAuth2.0’을 선택 합니다.

![&#xC778;&#xC99D;&#xBC29;&#xC2DD; - OAuth2.0](../../../.gitbook/assets/image%20%2848%29.png)

> * Grant Type
>
>        ‘Authorization Code’를 선택 합니다.
>
> * Client ID
>
>        앱의 API Key 값을 입력 합니다. \(자동 입력\)
>
> * Client Secret
>
>        앱의 Secret 값을 입력 합니다. \(자동 입력\)
>
> * Scope
>
>        앱에 등록한 Scope 값을 입력 합니다
>
> * Authorize Endpoint
>
>        [https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/authorize](https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/authorize) 값을 입력 합니다.
>
> * Token Endpoint
>
>        [https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/token](https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/token)   값을 입력 합니다.

‘OK’ 버튼을 누르시면 사용자 로그인창이 오픈 되며, 아이디 및 비밀번호를 입력하시고 로그인 합니다.   
아이디와 비밀번호\(OTP번호\)는 금융투자 핀테크 포털 가입 시 등록한 것이며, 테스트를 위해 별도로 부여되며 추가적인 고유 계정이 필요하시면 관리자에게 문의하십시오.

{% hint style="success" %}
**가상증권사 테스트계정   
 :** 코스콤 개발자센터 -&gt; API문서 &gt; 계좌서비스 -&gt; [가상증권사용 테스트 데이터 참조](https://developers.koscom.co.kr/documentation/account)
{% endhint %}

![&#xB85C;&#xADF8;&#xC778;](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9n-1MugBfAycrCN1bv%2F-LAHVaBFz-1K1zgJ-1hK%2F-LAHVdgooH8OWxGIrGxD%2Fimage.png?alt=media&token=079a6f64-0e4f-46fc-a15a-16eebc031b90)

테스트할 API를 선택 하시고 ‘Try it Out’ 버튼을 누르면 아래와 같이 Response결과를 받아 보실 수 있습니다.

![Response &#xACB0;&#xACFC;](../../../.gitbook/assets/image%20%2823%29.png)

‘Query’ 을 누르시면 Request 및 다양한 개발언어별 샘플코드를 참고 하실 수 있습니다.

![Query &#xD0ED;](../../../.gitbook/assets/image%20%2885%29.png)

