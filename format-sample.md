# format sample \(GET\)

KOSPI/KOSDAQ등의 지수 예상지수 및 업종별 투자자별 거래량등을 제공한다.  


#### Syntax {#syntax}

* HTTP methods
  * **GET**
* Authentication
  * **API Key**

{% hint style="info" %}
업종지수  스트리밍 조회는 xx를 참고하세요.
{% endhint %}



**Reference**

> * `marketcode`  
>   * 코드표 &gt; 시장코드표 참조
> * `issuecode`
>   * ex\) KR4101C90009 → **K101C9000**
>   * 코드표 &gt; 시장코드표 참조    ****
>   * 연결선물코드 추가 \(issuecode / 종목코드\)
>
>      - 선물최근월물의  종목히스토리 조회를 위해  사용가능
>
>      - 현재가 조회시 조회결과 종목코드는 현재기준시장에서 거래되는 종목의 단축종목코드로 결과를 보내줌





## 업종 종가

{% api-method method="get" host="https://sandbox-apigw.koscom.co.kr/v2/market/index" path="/{marketcode}/{issuecode}/closeprice" %}
{% api-method-summary %}
 /v2/market/index/{marketcode}/{issuecode}/closeprice
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marketcode" type="string" required=true %}
시장코드
{% endapi-method-parameter %}

{% api-method-parameter type="string" required=true name="issuecode" %}
업종코드 ex\) K1
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
ddddd
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```yaml
{
   "error": "당일 종가 제공 시간이 아닙니다." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Response Parameters {#request-parameters}

| **Name** | **Type** | **Description** |  |
| --- | --- | --- | --- | --- | --- |
| fundcode | String\(20\) | 펀드표준코드 |  |
| fundName | Number\(1\) | 펀드이름 |  |
| valAtTrade | ​string\(11\) | 잔고거래내역 | \*테이블 하단 참고 |
| varAtCur | string\(5\)​ | 잔고구분 | \*테이블 하단 참고 |
| qrToDate | String\(12\) | 조회종료날짜 | YYYYMMDD |

> * varAtTrade : 잔고거래내역
>   *  첫 요청은 null\(“null”\)로 표기하고, 다음 페이지부터는 response에서 주는 page 값을 넣어 요청하며, ALL인 경우는 page없이 일괄전송이므로 본 필드는 의미 없음
> * varAtCur : 잔고구분
>   * NRM\(일반/현금\), CRD\(신용\), LOAN\(대출\), SUM \(분류가 불가한 경우 구분 없이 합산한 경우며 대출잔고는 제외\)

#### ​ {#undefined-1}



