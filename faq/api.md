# API 사용절차

## 오픈 API 사용 자격은 무엇인가요?

&#x20;중소기업 중 핀테크산업 유관업종의 법인 또는 전자금융업자, 전자금융 보조업자(전자금융거래법상)이면 사용이 가능합니다. 다만, 본 오픈API를 이용하여 영위하려는 서비스가 사행성 또는 미풍양속에 저해되는 것을 방지하고자 사전 사업계획서(서비스설명서) 제출을 통하여 사전 사용승인 절차를 진행하고 있습니다.

{% content-ref url="../how-to-use/procedure/charge.md" %}
[charge.md](../how-to-use/procedure/charge.md)
{% endcontent-ref %}

{% hint style="warning" %}
**오픈API 플랫폼(개발자센터)  이용 대상** \
****\
****1. 이용 대상   (법인에 한정)\
「중소기업기본법」상 중소기업 중 아래의 하나에 해당하는 기관 \
\-   금융위원회의 핀테크산업 분류업종 업체 \
\-   전자금융업자 또는 전자금융보조업자 \
\-   기타 회사가 필요하다고 인정되는 업체 \
\
2\. 제외 대상 \
「사행행위 등 규제 및 처벌 특례법」상 사행행위업체 \
\-   부도, 금융질서문란업체 \
\-   대기업 출자 또는 소유업체 \
\-   불법행위 사업모델 업체 \
\-   사업모델 상 필요 자격 미달업체&#x20;
{% endhint %}

## 오픈 API 종류는 무엇이 있나요?

* 증권/파생시장 시세조회
* 자본시장 시세조회(주식, 선물/옵션 등) etc.

상세한 API 종류 정보는 다음 페이지에서 확인하세요.

{% content-ref url="../api/" %}
[api](../api/)
{% endcontent-ref %}

## API 서비스 사전검증통과는 어떻게 하고 어떤 서류가 필요하나요?

샌드박스(테스트환경)에서 먼저 개발 및 테스트를 완료한 뒤 상용(운영) 서비스로 전환 시에 필요한 절차입니다. 서비스에 대한 설명 자료 및 보안 취약점 점검 문서 등이 필요 합니다.&#x20;

자세한 사항은 코스콤 오픈API플랫폼 담당자 김동범 차장 (02-767-7913, imaro@koscom.co.kr) 으로 연락 바랍니다.

## 플랫폼 이용 적격여부 검토는 무엇을 심사하는 것인가요?

제출한 서류 검토 및 필시요 실사하여 심사하며, 사용하는 API 유형(금융거래, 비금융거래)에 따라 심사 내용이 다를 수 있습니다.

## 이용기관 등록 및 검증 등이 포함된 절차들이 걸리는 시간이 궁금합니다.

기업에 따라 상의 하겠으나, 대략 1-2달 이상이 소요 되는 것으로 보입니다. 단 비금융 거래의 경우 서비스 개발이 완료 후 계약 진행에 따라 단기간에 완료 될 수 있습니다.

## **모바일 개발용으로 제공하는 API가 있나요? 만약에 있다면 API 이용료가 따로 있나요?** <a href="#api-2" id="api-2"></a>

별도 모바일 개발 전용 API는 없습니다.&#x20;

자세한 사항은 [https://koscom.gitbook.io/open-api/api](https://koscom.gitbook.io/open-api/api) API 문서를 참조하세요.

## **API 이용시 준비해야 할 서류 및 상세 내용을 안내받을 수 있나요?** <a href="#api-3" id="api-3"></a>

{% content-ref url="../how-to-use/" %}
[how-to-use](../how-to-use/)
{% endcontent-ref %}

## API Key를 통해 API 테스트는 어떻게 진행하나요?

시세라이센스계약 및 오픈API플랫폼 이용신청을 하신 뒤에 코스콤 담당자로부터 샌드박스(테스트)용 API Key를 전달받으셨을 것입니다. 이를 활용하여 RESTful API 표준에 맞추어 API를 호출하시면 됩니다. 이 때 인증방식은 API key authentication 입니다. 자세한 사항은 아래 링크를 참조하세요.

[https://koscom.gitbook.io/open-api/how-to-use/devcenter#api-key-api-key-authentication](https://koscom.gitbook.io/open-api/how-to-use/devcenter#api-key-api-key-authentication)
