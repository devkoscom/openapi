# Implict

이 OAuth 방식은 핀테크 서비스의 최종 단말\(앱, 브라우저 등\)에서 직접 데이터소유자가 데이터접근동의를 하고 access token을 받아 단말 프로그램에서 API를 호출하는 구조에 적합합니다.

따라서 응답으로 온 데이터를 주로 화면에 출력하는 비즈니스 모델에 사용됩니다. 발급된 access token의 유효시간을 연장시키는 refresh token은 지원되지 않으며 access token의 유효시간이 만료되면 데이터접근동의절차를 다시 수행해야 합니다.

{% hint style="danger" %}
현재 **Implicit grant type을 지원하는 API는 없습니다.**    
향후 본 인증체계를 사용하게 되는 경우에 상세 내용을 제공하겠습니다.
{% endhint %}



![Implicit Grant Flow &#xC808;&#xCC28;](../../.gitbook/assets/image%20%2853%29.png)

