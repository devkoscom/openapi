---
description: 제공 중인 API 서비스
---

# API

Here are the articles in this section:

{% page-ref page="undefined/" %}

{% page-ref page="undefined-1.md" %}

{% page-ref page="undefined-2.md" %}

{% page-ref page="untitled-1-1/" %}

## 

오픈플랫폼에서 제공하고 있는 API는 크게 **1. 금융거래정보** 를 받기 위한 것과  **2. 기타 정보** 를 전달하기 위한 것으로 나뉩니다.

금융거래정보 API는 주로 금융회사의 계좌를 기반으로 하고 있으며, 관련 법령에 따라 본인 동의절차를 거쳐 제3자에게 제공되어야 하기 때문에 추가적인 권한확인 절차가 요구됩니다.   
계좌기반 API를 사용하여 개발한 서비스는 요청 메시지의 키가 되는 실계좌번호를 노출시키지 않고, 안전하게 제3자에게 제공하기 위해 서비스 이용자\(최종사용자;end user\)가 금융투자 핀테크 포탈에 가입하여 가상계좌번호를 발급하고, 금융거래정보 제3자 제공 동의서를 작성한 후 가상계좌번호를 사용하고자 하는 핀테크 서비스에 연결하는 선행과정이 필요합니다. 그리고 핀테크 서비스가 해당 API를 이용하려고 시도하는 과정에서 서비스 이용자의 확인과정이 개입됩니다.   
계좌기반 API를 제외한 나머지 API는 금융투자 핀테크 포탈 가입 여부와 관계없이 오픈플랫폼에 등록이 된 핀테크 기업의 경우 이용자에게 서비스를 제공할 수 있습니다.

단, 주문 및 일임매매 관련 API는 투자일임업 라이선스를 보유한 법인만 사용 가능 합니다.

제공 중인 API 유형은 다음과 같습니다.



## A. 공통서비스

### 1. 오픈플랫폼 가입여부 확인

{% tabs %}
{% tab title="기능\(데이터\)" %}
**핀테크 서비스 이용자가 오픈플랫폼 회원인지 확인하기 위한 API** 

가상계좌번호 발급, 정보제공동의서 작성 등 사전절차 안내 필요 여부 확인用
{% endtab %}

{% tab title="제공구간" %}
오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
오픈플랫폼 \(일반정보\)
{% endtab %}
{% endtabs %}

### 2. 가상계좌 목록 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**핀테크 서비스 이용자가 발급받은 가상계좌번호 목록을 금투사 名과 함께 제공**

금투사名과 가상계좌목록을 핀테크 서비스 App에 출력하여 이용할 계좌를 간편하게 선택할 수 있도록 함
{% endtab %}

{% tab title="제공구간" %}
오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
오픈플랫폼 \(일반정보\)
{% endtab %}
{% endtabs %}

{% page-ref page="undefined/" %}



## B. 계좌 서비스

### 1. 자산 포트폴리오 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**투자자의 자산내역\(증권, 파생, 펀드, 기타 금융상품\)을 보유비율\(구성비\)로 제공**

자산 상세내역\(투자금액, 보유주식수 등을 노출시키지 않고, 자산의 구성 비율만 부담 없이 제공할 수 있게 함으로써 투자성향분석 등 자문의 기초자료로 활용 가능
{% endtab %}

{% tab title="제공구간" %}
금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(민감도 낮은 금융정보\)
{% endtab %}
{% endtabs %}

### 2. 관심종목 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**투자자가 HTS 등에 등록해 놓은 관심종목 리스트를 조회할 수 있는 기능**

투자자가 관심을 보이는 종목에 대해 뉴스, 분석정보, 이벤트\(급등락, 공시 등\)의 정보를 능동적으로 제공할 수 있는 기초자료로 활용 가능
{% endtab %}

{% tab title="제공구간" %}
 금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
 금투사 \(민감도 낮은 금융정보\)
{% endtab %}
{% endtabs %}

### 3. 계좌잔고 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**투자자의 자산내역을 보유종목, 보유수량, 손익, 예탁금 등으로 상세하게 제공**

통합자산관리, 자문서비스를 위한 기본정보, 향후 주문서비스 확대 시 자산변동 실시간 조회용으로 활용 
{% endtab %}

{% tab title="제공구간" %}
 금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
 금투사 \(민감도 **높은** 금융정보\)
{% endtab %}
{% endtabs %}

### 4. 거래내역 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**금융상품의 매수, 매도, 현금입출금 내역을 지정한 기간별로 조회하기 위한 API**

투자성향 분석, 매수/매도 시점 분석을 통해 거래행태에 대한 자문 가능
{% endtab %}

{% tab title="제공구간" %}
 금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
 금투사 \(민감도 **높은** 금융정보\)
{% endtab %}
{% endtabs %}

{% page-ref page="undefined-1.md" %}



## **C. 주문 서비스**

### 1. 신규주문

{% tabs %}
{% tab title="기능\(데이터\)" %}
**신규 주문 제출**

증권사 마다 주문번호 부여 기준이 다를 수 있고, List 주문은 지원 하지 않음
{% endtab %}

{% tab title="제공구간" %}
금투사 &lt;-&gt; STB-HUB &lt;-&gt; 오픈플랫폼 &lt;-&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}

### 2. 주문취소

{% tabs %}
{% tab title="기능\(데이터\)" %}
**제출된 주문 취소**

List 취소 주문은 지원 하지 않음
{% endtab %}

{% tab title="제공구간" %}
금투사 &lt;-&gt; STB-HUB &lt;-&gt; 오픈플랫폼 &lt;-&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}

### 3. 주문정정

{% tabs %}
{% tab title="기능\(데이터\)" %}
**제출된 주문 정정**

가격 정정 : 일부 정정은 불가, 잔량 전체 지정  
수량 정정 : 수량 증가 불가
{% endtab %}

{% tab title="제공구간" %}
 금투사 &lt;-&gt; STB-HUB &lt;-&gt; 오픈플랫폼 &lt;-&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}



## D. 일임매매 서비스

### 1. 주문체결 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**금융상품의 주문 및 체결된 정보를 조회하기 위한 API**
{% endtab %}

{% tab title="제공구간" %}
금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}

### 2. 일임계좌 잔고 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**자산내역을 보유종목, 보유수량, 손익 등으로 상세하게 제공하기 위한 API**
{% endtab %}

{% tab title="제공구간" %}
  금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}

### 3. 결제 예정 정산 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
 **매매 정리된 정보를 통해 결제예정 사항을 확인하기 위한 API**
{% endtab %}

{% tab title="제공구간" %}
 금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}

### 4. 일임 설정계좌 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**일임매매 기관의 일임설정 계좌에 대한 정보를 제공하기 위한 API**
{% endtab %}

{% tab title="제공구간" %}
 금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}

### 5. 일임계좌 거래내역 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**금융상품의 매수, 매도, 현금입출금 내역을 지정한 기간별로 조회하기 위한 API**
{% endtab %}

{% tab title="제공구간" %}
 금투사 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
금투사 \(일임형 자문업자만 사용 가능\)
{% endtab %}
{% endtabs %}

{% page-ref page="undefined-2.md" %}



## E. 시세 서비스

### 1. 유가증권 및 코스닥 시세 조회

{% tabs %}
{% tab title="기능\(데이터\)" %}
**종목리스트 조회 API  
종목마스터 데이터 조회 API**  \(종목명, 상하한가, 전일거래량, 기준가 등\)  
**종목별 과거 데이터 조회 API** \(일, 주 및 월별 과거 시세 제공\)  
**투자자별 종가 정보 조회 API** \(투자주체별 매수/매도 거래량, 거래대금\)  
**종목별 호가 정보 조회 API  
종목별 체결 정보 조회 API**     \(현재가, 체결량, 누적거래량\)
{% endtab %}

{% tab title="제공구간" %}
 한국거래소 -&gt; 코스콤 -&gt;오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
코스콤 \(일반정보\)
{% endtab %}
{% endtabs %}

### 2. 선물시세 조회 

{% tabs %}
{% tab title="기능\(데이터\)" %}
**종목리스트 조회 API  
종목마스터 데이터 조회 API** \(종목명, 상하한가, 전일거래량, 기준가 등\)  
**종목별 과거 데이터 조회 API** \(일, 주 및 월별 과거 시세 제공\)  
**종목별 호가 정보 조회 API  
종목별 체결 정보 조회 API** \(현재가, 체결량, 누적거래량\)
{% endtab %}

{% tab title="제공구간" %}
   한국거래소 -&gt; 코스콤 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
 코스콤 \(일반정보\)
{% endtab %}
{% endtabs %}

### 3. 옵션시세 조회 

{% tabs %}
{% tab title="기능\(데이터\)" %}
**종목리스트 조회 API  
종목마스터 데이터 조회 API**  \(종목명, 상하한가, 전일거래량, 기준가 등\)  
**종목별 과거 데이터 조회 API** \(일, 주 및 월별 과거 시세 제공\)  
**종목별 호가 정보 조회 API  
종목별 체결 정보 조회 API**     \(현재가, 체결량, 누적거래 \)
{% endtab %}

{% tab title="제공구간" %}
   한국거래소 -&gt; 코스콤 -&gt;오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
 코스콤 \(일반정보\)
{% endtab %}
{% endtabs %}

{% page-ref page="untitled-1-1/" %}



## F. 분석 서비스

### 1. 비씨카드 섹터별 지수 

{% tabs %}
{% tab title="기능\(데이터\)" %}
**국내 카드 가맹점들의 섹터별/월별 매출 거래 건수에 대한 지수 정보** 
{% endtab %}

{% tab title="제공구간" %}
비씨카드 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
비씨카드 \(일반정보\)
{% endtab %}
{% endtabs %}

### 2. 비씨카드 종목지수 \(제공예정\) 

{% tabs %}
{% tab title="기능\(데이터\)" %}
**카드 빅데이터 기반으로 상장 종목의 월별 매출 추세를 추산한 지수**
{% endtab %}

{% tab title="제공구간" %}
비씨카드 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
비씨카드 \(일반정보\)
{% endtab %}
{% endtabs %}

### 3. RA테스트베드 알고리즘 

{% tabs %}
{% tab title="기능\(데이터\)" %}
**알고리즘 목록조회  
알고리즘 운용실적  
알고리즘 위험 및 성과지표**
{% endtab %}

{% tab title="제공구간" %}
코스콤 -&gt; 오픈플랫폼 -&gt; 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
코스콤/RA테스트베드 사무국 \(일반정보\)
{% endtab %}
{% endtabs %}

### 4. BIGBOT

{% tabs %}
{% tab title="기능\(데이터\)" %}
**종목분석  
투자성향 조사  
포트폴리오 추천 및 평가  
자산배분**
{% endtab %}

{% tab title="제공구간" %}
핀테크 -&gt; 오픈플랫폼 -&gt; 핀테크****
{% endtab %}

{% tab title="제공주체\(속성\)" %}
핀테크/빅트리 \(일반정보\)
{% endtab %}
{% endtabs %}



## G. 뉴스 서비스

### 1. 금융뉴스 검색

{% tabs %}
{% tab title="기능\(데이터\)" %}
**통합 시세조회 서비스 API  
금융 뉴스검색 API \(키워드, 분야별\)**
{% endtab %}

{% tab title="제공구간" %}
핀테크 -&gt; 오픈플랫폼 -&gt; 금투사, 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
핀테크/위버플 \(일반정보\)
{% endtab %}
{% endtabs %}



## H. 재무 서비스

### 1. 재무정보 제공 \(BSMIT\)

{% tabs %}
{% tab title="기능\(데이터\)" %}
**종목별 영업이익률 조회 API  
업종별 평균 영업이익률 조회 API  
금액별 포트폴리오  
파봇랭크**
{% endtab %}

{% tab title="제공구간" %}
핀테크 -&gt; 오픈플랫폼 -&gt; 금투사, 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
핀테크/BSMIT \(일반정보\)
{% endtab %}
{% endtabs %}

### 2. 재무정보 제공 \(위버플\)

{% tabs %}
{% tab title="기능\(데이터\)" %}
**기업정보 조회 API \(재무 데이터\)**
{% endtab %}

{% tab title="제공구간" %}
핀테크 -&gt; 오픈플랫폼 -&gt; 금투사, 핀테크
{% endtab %}

{% tab title="제공주체\(속성\)" %}
핀테크/위버플 \(일반정보\)
{% endtab %}
{% endtabs %}





{% hint style="info" %}
모든 API 는[ 코스콤 개발자센터](https://developers.koscom.co.kr) 에서 이용할 수 있습니다.
{% endhint %}

{% hint style="warning" %}
해당 온라인 공용매뉴얼에 기술되지 않은 **기타 API** 관련 매뉴얼은   
'코스콤 개발자 센터 &gt; API 문서 &gt; [참조문서](https://developers.koscom.co.kr/documentation/reference)’ 에서 확인하세요.
{% endhint %}



