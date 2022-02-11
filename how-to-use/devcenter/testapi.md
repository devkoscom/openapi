# API 테스트

본 페이지에서는 **API를 호출하기 위한 개발자센터에서 테스트 하는 절차**를 다룹니다.&#x20;

'APIs & 플랜' 메뉴에서 테스트 하려는 API의 인증유형을 확인합니다.

![APIs 메뉴](<../../.gitbook/assets/image (7).png>)

{% hint style="info" %}
인증에 대한 상세한 설명을 원하실 경우 [이곳](https://koscom.gitbook.io/open-api/authentication)을 참조하세요.
{% endhint %}



## API Key Authentication

'API문서 > 시세 서비스 > 주식종목' 메뉴에서 'Select an Application' 을 눌러서 앱을 선택 합니다.\
앱이 보이지 않으시면 해당 API를 사용하는 앱을 먼저 만드셔야 합니다. 애플리케이션 등록 방법은 [이곳](https://koscom.gitbook.io/open-api/how-to-use/devcenter/enrollapp)을 참조하세요.

![Authentication 방식 선택](<../../.gitbook/assets/image (125).png>)

‘Authentication (None)’ 버튼을 __ 누르시고, 인증방식을 ‘API Key’로 선택 합니다.

![인증방식 선택](<../../.gitbook/assets/image (42).png>)

'API Key Type'은 해당 API의 Method가 **GET방식**이면 **Query**로 선택 하시고,  **POST방식**이면 **Header**로 선택 하세요.

![인증방식 - API Key](<../../.gitbook/assets/image (86).png>)

테스트할 API를 선택 하시고 'Try it Out' 버튼을 누르시면 아래와 같이 Response 결과를 받아 보실 수 있습니다.

![Response 결과](<../../.gitbook/assets/image (143).png>)

'Query' 탭을 누르시면 Request 및 다양한 개발언어별 샘플코드를 참고 하실 수 있습니다.

![Query 탭](<../../.gitbook/assets/image (29).png>)



## Basic  Authentication&#x20;

'API문서 > 일임매매서비스 > XX증권-일임매매서비스' 메뉴에서 'Select an Application' 을 눌러서 앱을 선택 합니다. 앱이 보이지 않으시면 해당 API를 사용하는 앱을 먼저 만드셔야 합니다. 애플리케이션 등록 방법은 [이곳](https://koscom.gitbook.io/open-api/how-to-use/devcenter/enrollapp)을 참조하세요.

![앱 선택](<../../.gitbook/assets/image (92).png>)

‘Authentication (None)’ 버튼을 __ 누르시고, 인증방식을 'HTTP Basic'으로 선택 합니다.

![Basic 인증방식 선택](<../../.gitbook/assets/image (42).png>)

Username과 Password 항목에 등록한 어플리케이션의 API Key값과 Secret 값을 입력합니다.&#x20;

![인증방식 - Basic](<../../.gitbook/assets/image (145).png>)

> *   Username
>
>     &#x20;    앱의 API Key 값을 입력 합니다.
> *   Password
>
>     &#x20;    앱의 Secret 값을 입력 합니다.

테스트할 API를 선택 하시고 'Try it Out' 버튼을 누르시면 아래와 같이 Response 결과를 받아 보실 수 있습니다.

![Response 결과](<../../.gitbook/assets/image (138).png>)



## OAuth 2.0

{% hint style="warning" %}
현재는 OAuth2.0 Grant Type 중 **Authorization Code 만 지원**하며, \
Implicit Grant Type 등은 보안수준 및 비즈니스모델에 따라 협의가 필요합니다.&#x20;
{% endhint %}

![앱 선택](<../../.gitbook/assets/image (11).png>)

'APIs & 플랜' 메뉴에서 OAuth2.0-Authorization Code를 지원하는 API를 확인 합니다.&#x20;테스트할 앱을 선택하고 'OAuth2.0'을 선택 합니다.

![인증방식 - OAuth2.0](<../../.gitbook/assets/image (82).png>)

> *   Grant Type
>
>     &#x20;    'Authorization Code'를 선택 합니다.
> *   Client ID
>
>     &#x20;    앱의 API Key 값을 입력 합니다. (자동 입력)
> *   Client Secret
>
>     &#x20;    앱의 Secret 값을 입력 합니다. (자동 입력)
> *   Scope
>
>     &#x20;    앱에 등록한 Scope 값을 입력 합니다>     &#x20;( \* [Scope](https://koscom.gitbook.io/open-api/authentication/oauth/scope) 페이지 참조 )
> *   Authorize Endpoint
>
>     &#x20;    [https://sandbox-apigw.koscom.co.kr/auth/oauth/v3/authorize](https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/authorize) 값을 입력 합니다.
> *   Token Endpoint
>
>     &#x20;    [https://sandbox-apigw.koscom.co.kr/auth/oauth/v3/token](https://sandbox-apigw.koscom.co.kr/auth/oauth/v2/token)   값을 입력 합니다.>

'OK' 버튼을 누르시면 사용자 로그인창이 오픈 되며, 아이디 및 비밀번호를 입력하시고 로그인 합니다. \
아이디와 비밀번호(OTP번호)는 금융투자 핀테크 포털 가입 시 등록한 것이며, 테스트를 위해 별도로 부여됩니다. 추가적인 고유 계정이 필요하시면 관리자에게 문의하십시오.

{% hint style="success" %}
**가상증권사 테스트계정**&#x20;\
&#x20;**:** 코스콤 개발자센터 -> API문서 > 계좌서비스 -> [가상증권사용 테스트 데이터 참조](https://developers.koscom.co.kr/documentation/account)
{% endhint %}

![로그인](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9n-1MugBfAycrCN1bv%2F-LAHVaBFz-1K1zgJ-1hK%2F-LAHVdgooH8OWxGIrGxD%2Fimage.png?alt=media\&token=079a6f64-0e4f-46fc-a15a-16eebc031b90)

테스트할 API를 선택 하시고 ‘Try it Out’ 버튼을 누르면 아래와 같이 Response결과를 받아 보실 수 있습니다.

![Response 결과](<../../.gitbook/assets/image (39).png>)

‘Query’ 탭을 누르시면 Request 및 다양한 개발언어별 샘플코드를 참고 하실 수 있습니다.

![Query 탭](<../../.gitbook/assets/image (152).png>)



## API Key \&Secret 조회 방법

> 등록한 애플리케이션(앱) 의 API Key 및 Secret 조회하는 방법

'대시보드 > 어플리케이션' 으로 이동 후, 등록한 애플리케이션의 '설정' 버튼을 클릭합니다.  그 뒤 '편집' 탭을 선택합니다.

![애플리케이션 편집](<../../.gitbook/assets/image (126).png>)

인증 탭에서 Key와 Secret 버튼을 클릭하면 애플리케이션의 API Key와 Secret을 확인할 수 있습니다.&#x20;

![인증 탭](<../../.gitbook/assets/image (9).png>)

