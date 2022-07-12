# API 서비스

## **API Gateway Domain**

> `{APIGWAddr}`

#### **Production**(상용)      |  `oap.k-mydata.org`

#### **Sandbox**(샌드박스)  |  `testoap.k-mydata.org`

## 공통 URI

**URI   |** **`https://`**_**`{APIGWAddr}/{버전 정보}/{서비스 구분}/{API 구분}?[QueryString]`**_

API는 버전으로 구분되기 때문에 URI에 버전정보가 포함되어 있습니다.

현재 v3 버전이 제공 중입니다.

{% hint style="success" %}
`{APIGWAddr}` : 오픈API플랫폼 Gateway 주소
{% endhint %}

&#x20;오픈플랫폼에서 제공하고 있는 제공 중인 API 유형은 다음과 같습니다.

### 시세 서비스

#### 주식

* 주식실시간종가A
* 주식실시간종가B
* 주식실시간종가C
* 주식실시간A
* 주식실시간B

#### 파생

* 파생실시간종가A
* 파생실시간A

#### 업종

* KRX업종실시간종가
* KRX업종실시간

#### 기타

* 유가종목별투자자
* 코스닥종목별투자자
* 부가서비

{% hint style="info" %}
한국거래소 -> 코스콤 ->오픈플랫폼 -> 핀테크업

_**코스콤 (**<mark style="color:blue;">**정보시세 라이센스 계약 필요**</mark>**)**_
{% endhint %}

{% content-ref url="marketv3/" %}
[marketv3](marketv3/)
{% endcontent-ref %}

###

### 재무 서비스

#### NICE-기업정보

* 기업개요 정보를 조회
* 기업재무분석정보를 조회
* 기업재무정보 상태표를 조회

{% hint style="info" %}
_**NICE평가정보 제공**_
{% endhint %}



