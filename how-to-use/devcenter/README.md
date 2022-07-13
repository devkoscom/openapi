# API 테스트 절차

오픈API플랫폼에서 제공하는 API서비스에 대한 개발 및 테스트를 위해서는  **API Key** 발급을 완료 하여야 합니다.

사전에 시세라이센스 계약을 먼저 진행하신 후, 오픈API플랫폼 계약 시 아래 4가지 신청 서류를 작성하여 open@koscom.co.kr 으로 이메일 발송하여 주시면 관리자에 의한 승인 절차가 진행됩니다. 승인이 완료되면 샌드박스 환경 (테스트용) API Key를 제공합니다.



## API 이용신청

API 이용 신청 및 Sandbox(테스트용) API Key 발급

1.  **API 및 서비스 사전검증**

    API구독(사용) 또는 API게시(제공) 서비스의 자본시장 발전과 관련 여부 검토

    사행성, 미풍양속의 저해여부 등 검토\

2.  **시세라이센스 계약** _(시세API서비스 이용 시)_\
    문의 : 코스콤 시장정보영업팀 이상원 수석 (E : [success@koscom.co.kr](mailto:success@koscom.co.kr), T : 02-767-7574)

    ​
3.  **오픈API플랫폼 계약 및 이용적격여부 검토**\
    ****문의 : 코스콤 API플랫폼팀 (E : <mark style="color:blue;">open@koscom.co.kr</mark> 및 <mark style="color:blue;">imaro@koscom.co.kr</mark>, T : 02-767-7913)\


    \* 오픈API플랫폼 신청 서류 \*

    1. _오픈API플랫폼 사용 신청서 1 부_
    2. _법인등기부 등본 1부_
    3. _사업자 등록증 1부_
    4. _서비스 계획서 (자유 양식) 1부. 끝_\
       __
4. **최종 승인 및 회원사 공지**\
   ****샌드박스(테스트)환경 API Key 발급 후 전달\
   추후 샌드박스(테스트) 환경에서 테스트가 완료되면 실가동(Production/운영)환경 API KEY 전달

{% file src="../../.gitbook/assets/오픈API플랫폼_사용_신청서.doc" %}

{% hint style="danger" %}
오픈API플랫폼은 **"법인"**기업만 이용 가능합니다. \
개인사업자, 일반인, 학생 등은 이용할 수 없습니다.
{% endhint %}

{% hint style="info" %}
코스콤 오픈API플랫폼 시세API 서비스를 이용하시기 위해서는 **사전에  "시세라이센스 계약"이 선행**되어야 합니다.\


* 정보시세 라이센스 계약 문의처\
  이메일   |    <mark style="color:blue;">success@koscom.co.kr</mark>\
  전화       |    02-767-7574\

* 오픈API플랫폼 이용 문의처\
  &#x20;이메일  |    [open@koscom.co.kr](mailto:open@koscom.co.kr) , <mark style="color:blue;">imaro@koscom.co.kr</mark>\
  &#x20;전화      |    02-767-7913
{% endhint %}



## Sandbox 테스트 환경 안내

**샌드박스 환경에서 제공되는 시세 데이터는 개발 지원용으로만 제공되므로 데이터 정합성이 맞지 않을 수 있습니다.**

현재 코스콤에서 제공되는 실시간 제공 시세와 자료가 상이할 수 있으며, 제공되는 서비스는 시스템 점검등으로 별도 고지 없이 중단될 수 있습니다.

개발 지원용 시세 데이터라 할지라도 데이터의 가공 또는 축적을 위해서는 코스콤의 정보시세 라이센스가 필요한 것으로써 **'**정보시세 라이센스' 계약이 수반되어야 시세 데이터의 가공 또는 축적이 가능합니다.\




## API KEY 인증방식

> _API Key Authentication_

API Key Authentication만을 사용하는 API는 주로 **민감정보가 포함되지 않은** 데이터를 요청•응답하는 경우이며, 핀테크 서비스를 등록할 때 받은 `API Key`만으로 API 호출권한을 확인하게 됩니다.

HTTP method(GET, POST)에 따라 `API Key`를 전달하는 방식이 달라지며, GET일 경우는 API URL의 query parameter로 전달하고, POST방식은 HTTP header의 필드로 전달해야 합니다.&#x20;

### GET 방식

URL query parameter인 apikey에 넣어 전송

```powershell
curl -X GET \
  'https://testoap.k-mydata.org/v3/shemarket/realtime/kosdaq/stocks/247540/price?apikey=l7xxxxxxxxxxxxxx48c982eb192ac98e206'
```

### POST 방식

HTTP header의 apikey 필드에 API Key를 넣어 전송

```powershell
curl -X POST -H "apikey: l7xxxxxxxxxxxxxxxx46844861524b2320" -H "Content-Type: application/json" -H "Cache-Control: no-cache" -H 
 -d '{
  "partner": {
    "comId": "COMPANY-ID",
    "srvId": "CLIENT-ID"
  },
  "commonHeader": {
    "reqIdPlatform": "android",
    "reqIdConsumer": "tx-001",
    "certDn": "Ou=KOSCOM,blah",
    "ci": "35SA9SlOxR3vOSQF0aXztoWpwgLmXFZbH074ZcqwbPBCIwt4xo1I0az0lu7qp5nuDRs78QNJxAnZk5SP/XB8Yw=="
  },
  "body": {
    "korName": "홍길동"
  }
}' "https://testoap.k-mydata.org/v3/market/realtime/kosdaq/stocks/247540/price"
```



