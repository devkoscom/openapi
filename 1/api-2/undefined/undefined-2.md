---
description: 금융투자회사(증권사) 공통
---

# 증권사

현재 증권회사가 오픈플랫폼을 통해 제공하고 있는 API는 모두 계좌를 기반으로 하고 있습니다. 

따라서 핀테크 서비스 회원과 증권사 고객정보를 연결시킬 식별자가 필요하며 이를 휴대폰 본인확인 서비스를 통해 발급받은 **연계정보\(CI, Connecting Information\)**을 사용하고 있습니다. 또한 증권사의 실제 계좌번호와 1:1로 매핑된 **가상계좌번호**를 오픈플랫폼 금융투자 핀테크 포탈\([http://open.koscom.co.kr](http://open.koscom.co.kr)\)에서 발급하여 연계정보\(CI\)와 함께 API를 통한 요청의 키로 사용합니다.

핀테크업체가 핀테크 서비스를  증권사가 제공하는 계좌기반 API와 같이  금융거래정보가 전달되는 API를 사용하여 개발하였다면,  **핀테크 서비스 이용자\(end user\)는 사전에 금융투자 핀테크 포탈에 가입하여, 핀테크 서비스에 연결하고자 하는 증권사의 실계좌번호에 연결된 가상계좌번호를 발급받아야 하며**, 사용하고자 하는 핀테크 서비스에 가상계좌번호를 연결하는 과정이 선행되어야 합니다.

계좌기반 API를 사용하는 핀테크 서비스를 이용자\(end user\)가 사용하기 위해서는 사전에 위와 같은 이용조건을 충족했는지를 확인하는 것이 필요합니다. '금융투자 핀테크 포탈'에 가입하지 않은 이용자를 대상으로 핀테크포탈 가입을 유도해야 하며, 가입이 된 이용자라 하더라도 가상계좌발급을 받았는지 여부와 가상계좌를 핀테크 서비스에 연결하였는지를 확인할 수 있어야 합니다. 오픈플랫폼은 이를 확인하기 위한 [서비스연동 API](https://koscom.gitbook.io/open-api/~/edit/primary/1/api-2/undefined/undefined-2)를 제공하고 있습니다.





## API 호출  공통사항

**값 없음 표기 방법**  
 요청\(request\)    데이터  : 필수 필드이나 값이 없는 경우는 ""로 표기  
 응답\(response\) 데이터  : 필드 또는 블록이 없음\(null\), 필드 값이 null, 필드 값이 "null", 필드 값이 ""로 올 수 있으므로 null 체크 로직 구현 시 주의 필요 

**스펙 required 항목**   
 "필수"  :  값이 반드시 있어야 하거나, 적어도 값이 ""로라도 존재해야 하는 항목  
 "반환"  :  요청 시 값이 그대로 응답에 실려 돌아옴  
 "선택"  :  다른 항목의 구분 값에 따라 필수 항목인 경우를 의미

**숫자 표기**  
 Type의 괄호 안 숫자   :  권장 최대 길이   
 \[ \]안의 숫자                   :  길이가 지정된 항목   
 숫자 표기에서 0이 9개 이상 표기되어야 하는 경우 :  JSON 표기법 표준에 따라 Scientific notation 사용





## 조회 API  유의사항

조회 API는 **API에 지정된 가상계좌를 조회범위**로 하기 때문에 계좌속성\(위탁, 펀드, 파생상품 등\)에 따라 조회조건이 충족되지 않을 수 있으므로 전 상품군을 대상으로 조회할 경우는 주의가 필요합니다. 

보통 증권회사의 종합계좌는 모든 금융상품을 취급할 수 있는 것이지만 경우에 따라 파생상품과 같은 특정 상품군은 별도로 관리되는 증권회사도 있으며, 종합계좌 개념을 도입하지 않는 증권사도 존재합니다. 따라서 종합계좌라고 판단되어 KOSPI200 파생상품 잔고를 조회하였을 때 응답에 해당상품이 반드시 포함될 것이라 판단하고 비즈니스를 설계하면 안됩니다. 

자산포트폴리오조회와 계좌잔고조회의 경우 모든 상품군을 조회범위에 포함하는 ‘ALL’검색조건을 지원하는 증권사의 경우 해당 조건으로 계좌를 조회하면 문제가 없지만, ‘ALL’검색조건을 지원하지 않는 증권사의 경우 각 상품군별로  계좌를 대상으로 조회해야 누락 없이 전 상품군을 조회할 수 있습니다. 

{% hint style="success" %}
**가상증권사 테스트계정   
 :** 코스콤 개발자센터 -&gt; API문서 &gt; 계좌서비스 -&gt; [가상증권사용 테스트 데이터](https://developers.koscom.co.kr/documentation/account) 참조
{% endhint %}





## 증권사 API  종류

각 API에 대한 자세한 설명은 아래의 링크를 클릭하세요 :

{% page-ref page="../undefined-1.md" %}

{% page-ref page="../undefined-2.md" %}



