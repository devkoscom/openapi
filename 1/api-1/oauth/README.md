# OAuth

OAuth인증체계를 사용하는 API는 **민감정보가 포함된** 데이터를 요청•응답하는 경우이며, API호출 전에 **데이터 소유권자\(Resource Owner\)을 개입**시켜 정보접근의 승인을 받는 과정이 포함되어있습니다. 승인과정이 정상적으로 처리되면 오픈플랫폼은 API호출에 필요한 access token을 발급하며, 핀테크 서비스는 API를 호출할 때 access token을 포함시켜 전송하면 됩니다. 

오픈플랫폼에서 제공하는 OAuth버전은 2.0이며 핀테크 서비스의 유형과 보안수준에 따라 access token을 발급하는 방법이 구분됩니다. 인증방식에 대한 선택은 오픈플랫폼 관리자와 협의 후 결정하시면 되며, 비즈니스 모델과 보안수준에 따라 결정됩니다.

해당 인증방식은 2가지로 나눌 수 있습니다.

## 1. Authorization Code Grant Flow

> Server-Side Web Application Flow

이 방식은 데이터소유자\(Resource Owner, 서비스 이용자\)에게 데이터 접근에 대한 권한을 위임 받아 access token을 오픈플랫폼으로부터 받아오고, 만기\(expiration time\)을 갖는 access token을 갱신\(refresh token\)할 수 있는 권한도 부여 받아 데이터소유자의 승인과정 없이도 API를 통해 데이터에 접근할 수 있는 인증방식입니다. 

따라서 주로 서버 사이드의 웹 애플리케이션에서 API를 사용할 경우에 적합하며, 주기적으로 데이터소유자의 위임을 받아 데이터에 접근할 필요가 있는 비즈니스 모델에 사용됩니다. 

{% page-ref page="authorization-code-grant-flow.md" %}



## 2. Implicit Grant Flow

> Client-Side Web Application Flow

이 방식은 핀테크 서비스의 최종 단말\(앱, 브라우저 등\)에서 직접 데이터소유자가 데이터접근동의를 하고 access token을 받아 단말 프로그램에서 API를 호출하는 구조에 적합합니다. 

따라서 응답으로 온 데이터를 주로 화면에 출력하는 비즈니스 모델에 사용됩니다.

{% page-ref page="untitled-1.md" %}


