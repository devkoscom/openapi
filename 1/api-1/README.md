---
description: API 인증 방식
---

# 인증

사용하고자 하는 API에 따라 지정된 인증방식을 사용해야 하며 크게 3가지 방식으로 나눌 수 있습니다.

## 1. API Key Authentication

계좌기반API를 제외한 일반정보 API를 사용하는 경우 코스콤 개발자센터 \([https://developers.koscom.co.kr](https://developers.koscom.co.kr/)\)에 앱을 등록 완료 후 할당 받은 API Key를 지정된 Query parameter 혹은 HTTP header에 넣어 전송하고, 이를 오픈플랫폼에서 인증하는 방식

_자세한 설명은 아래의 링크를 클릭하십시오:_

{% page-ref page="api-key-authentication.md" %}

## 2. Basic Authentication

일임매매 전용 API를 사용하는 경우 코스콤 개발자센터 \([https://developers.koscom.co.kr](https://developers.koscom.co.kr/)\)에 앱을 등록 완료 후 할당 받은 API Key 및 Secret를 조합하여 Base64로 인코딩한 값을 지정된 HTTP header에 넣어 전송하고, 이를 오픈플랫폼에서 인증하는 방식

_자세한 설명은 아래의 링크를 클릭하십시오:_

{% page-ref page="basic-authentication.md" %}

## 3. OAuth

계좌기반 API를 사용하는 경우 코스콤 개발자센터 \([https://developers.koscom.co.kr](https://developers.koscom.co.kr/)\)에 앱을 등록 완료 후 할당 받은 API Key \(Client ID\), Client Secret와 개발자가 입력한 redirect\_uri 및 API별 scope를 지정된 HTTP header에 넣고, 추가로 API를 호출하기 전 이용자로부터 정보접근 동의를 받은 후 오픈플랫폼으로부터 제공받는 Access Token을 헤더에 포함시켜 인증을 받는 방식 

_자세한 설명은 아래의 링크를 클릭하십시오:_

{% page-ref page="oauth/" %}



