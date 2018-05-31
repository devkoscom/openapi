# API Key Authentication

API Key Authentication만을 사용하는 API는 주로 **민감정보가 포함되지 않은** 데이터를 요청•응답하는 경우이며, 핀테크 서비스를 등록할 때 받은 `API Key`만으로 API 호출권한을 확인하게 됩니다.

HTTP method\(GET, POST\)에 따라 `API Key`를 전달하는 방식이 달라지며, GET일 경우는 API URL의 query parameter로 전달하고, POST방식은 HTTP header의 필드로 전달해야 합니다. 

### GET 방식

URL query parameter인 apikey에 넣어 전송

```yaml
curl -X GET -H "Cache-Control: no-cache" -H 
"https://sandbox-apigw.koscom.co.kr/v2/market/stocks/kospi/list?apikey=l7xx230ef2235e34448c982eb192ac98e206"
```

### POST 방식

HTTP header의 apikey 필드에 API Key를 넣어 전송

```yaml
curl -X POST -H "apikey: l7xxf234248b6fbd42a1a6844861524b2320" -H "Content-Type: application/json" -H "Cache-Control: no-cache" -H 
 -d '{
  "partner": {
    "comId": "COMPANY-ID",
    "srvId": "CLIENT-ID"
  },
  "commonHeader": {
    "reqIdPlatform": "android",
    "reqIdConsumer": "tx-001",
    "certDn": Ou=KOSCOM,
    "ci": "35SA9SlOxR3vOSQF0aXztoWpwgLmXFZbH074ZcqwbPBCIwt4xo1I0az0lu7qp5nuDRs78QNJxAnZk5SP/XB8Yw=="
  },
  "body": {
    "korName": "홍길동"
  }
}' "https://sandbox-apigw.koscom.co.kr/v1/common/member/register/search"
```



{% hint style="info" %}
코스콤 개발자센터\(Sandbox\)   API Key 이용방법은  [이곳](https://koscom.gitbook.io/open-api/undefined-4/undefined-2/untitled#api-key) 을 참조하세요.
{% endhint %}



