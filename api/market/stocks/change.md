# 요구형항목

요구형항목은 **조회형** 또는 **실시간형** 데이터를 제공합니다.



## 조회

> 요구형항목 - 마스터데이타 조회\(주식\)

주식 종목별 마스터\(배치\) 정보에 대해 종복별 요청한 데이타 항목만 조회결과로 전송

주식종목마스터\(master\) 대비 다양한 종목기본정보 제공 \(최고가, 대차, 이동평균등 총 76개 항목\)  
고객 추가 요구사항 발생시 API 변경을 최소화하여 추가 데이타 제공



### 사용 방법

ex\) 삼성전자 전일종가와 52주 최고가격만 조회하고자 할 경우 

```swift
GET /v2/market/stocks/kospi/005930/selectivemaster?prevddClsprc&wk52HgstPrc
```

  

### **조회가능 데이터 항목**

> 마스터\(배치\) 데이터

| **Name** | **Type** | **Description** |  | **제공구분** |
| :--- | :--- | :--- | :--- | :--- |
| trdDd | string\(8\) | 체결일자,거래일자,매매일자 \( |  | ~/master, ~/selectivemaster |
| isuCd | string\(12\) | 종목코드 | 표준코드 | ~/master, ~/selectivemaster |
| isuSrtCd | string\(9\) | 종목단축코드 | 예\) KR7000660001 → 000660 | ~/master, ~/selectivemaster |
| isuKorAbbrv | string\(40\) | 종목한글약명 | 가나다 | ~/master, ~/selectivemaster |
| secugrpId | string\(2\) | 증권그룹ID | ST:주권 MF:증권투자회사 RT:부동산투자회사 SC:선박투자회사 IF:사회간접자본투융자회사 DR:주식예탁증서 EW:ELW EF:ETF SW:신주인수권증권 SR:신주인수권증서 BC:수익증권 FE:해외ETF FS:외국주권 EN:ETN 2014.11.17 | ~/master, ~/selectivemaster |
| mktWarnTpCd | string\(2\) | 시장경보구분코드 | 00:해당없음\(시장경보가 지정될 수 있는 종목에 대해서 지정된 바가 없음을 의미\) 01:투자주의 02:투자경고 03:투자위험 | ~/master, ~/selectivemaster |
| admisuYn | string\(1\) | 관리종목여부 | Y:관리 N:일반 | ~/master, ~/selectivemaster |
| haltYn | string\(1\) | 거래정지여부 | Y, N | ~/master, ~/selectivemaster |
| idxIndMidclssCd | string\(3\) | 지수업종중분류코드 | 업종분류, 상세코드는 업종코드표 참고 | ~/master, ~/selectivemaster |
| mktcapScaleCd | string\(1\) | 시가총액규모코드 | 유가\(0:제외 1:대 2:중 3:소\) 코스닥\(0:제외 1:KOSDAQ100 2:KOSDAQmid300 3:KOSDAQsmall\) | ~/master, ~/selectivemaster |
| mfindYn | string\(1\) | 제조업여부 | Y, N \(유가\)제조업여부 | ~/master, ~/selectivemaster |
| smeYn | string\(1\) | 중소기업여부 | Y, N \(코스닥\)중소기업여부 | ~/master, ~/selectivemaster |
| 업종 | string\(1\) | KRX100종목여부 | Y, N  | ~/master, ~/selectivemaster |
| kospiYn | string\(1\) | KOSPI여부 | Y, N \(유가\)KOSPI100여부,\(코스닥\)프리미어여부, 프리미어여부 추가 2009.11.16 | ~/master, ~/selectivemaster |
| kospi100Yn | string\(1\) | KOSPI100여부 | Y, N \(유가\)KOSPI여부 | ~/master, ~/selectivemaster |
| kospi50Yn | string\(1\) | KOSPI50여부 | Y, N \(유가\)KOSPI50여부 | ~/master, ~/selectivemaster |
| basPrc | number\(11\) | 기준가격,기준가액 |  | ~/master, ~/selectivemaster |
| prevddClsprc | number\(11\) | 전일종가 |  | ~/master, ~/selectivemaster |
| prevddAccTrdvol | number\(11\) | 상장중최저가일자 |  | ~/master, ~/selectivemaster |
| prevddAccTrdval | number\(22\) | 전일누적거래대금 |  | ~/master, ~/selectivemaster |
| uplmtprc | number\(11\) | 상한가 |  | ~/master, ~/selectivemaster |
| lwlmtprc | number\(11\) | 하한가 |  | ~/master, ~/selectivemaster |
| sbPrc | number\(11\) | 대용가격 | ST,FS,DR,MF,RT,SC,IF,ET,FE,BC,EN 만 해당 2014.11.17 | ~/master, ~/selectivemaster |
| parval | number\(11\) | 액면가 | 9\(9\)V9\(3\) 외국주권일 경우 소숫점셋째자리까지 표현가능 / 코스닥의 각국의 최소화폐단위 표시는 유가기준으로 통일 / ※ST,FS,RT,SC,BC만 해당" | ~/master, ~/selectivemaster |
| isuPrc | number\(11\) | 발행가격 | 신주인수권증서 포함 | ~/master, ~/selectivemaster |
| listDd | string\(8\) | 상장일자 | YYYYMMDD | ~/master, ~/selectivemaster |
| listShrs | number\(16\) | 상장주식수,상장증권수 |  | ~/master, ~/selectivemaster |
| arrantrdYn | string\(1\) | 정리매매여부 |  | ~/master, ~/selectivemaster |
| creditOrdPosblYn | string\(1\) | 신용주문가능여부 | Y, N | ~/master, ~/selectivemaster |
| regulssQtyUnit | number\(6\) | 정규장매매수량단위 |  | ~/master, ~/selectivemaster |
| invstcautnRemndIsuYn | string\(1\) | 투자주의환기종목여부 | Y, N | ~/master, ~/selectivemaster |
| srttrmOverheatIsuTpCd | string\(1\) | 단기과열종목구분코드 | 0:해당없음 /1:지정예고 /2:지정 /3:지정연장\(해제연기\) 2012.11.05 추가 | ~/master, ~/selectivemaster |
| eps | number\(11\) | 주당순이익 |  | ~/master, ~/selectivemaster |
| per | number\(11\) | 주가수익률 |  | ~/master, ~/selectivemaster |
| bps | number\(11\) | 주당순자산가치 |  | ~/master, ~/selectivemaster |
| pbr | number\(11\) | 주당순자산비율 |  | ~/master, ~/selectivemaster |
| dps | number\(11\) | 주당배당금액 |  | ~/master, ~/selectivemaster |
| divYd | number\(11\) | 배당수익율 |  | ~/master, ~/selectivemaster |
| acntclsCd | string\(12\) | 결산월구분 | 월별 Map 구조 \(001001001001 =&gt; 3,6,9,12 월\) | ~/master, ~/selectivemaster |
| adjStkprcCalcYn | string\(1\) | 수정주가산출여부 | Y, N | ~/master, ~/selectivemaster |
| prevddNav | number\(22\) | 전일순자산가치 | ETF종목일 경우 소수점 2자리로 표현, 일반종목은 0 | ~/master, ~/selectivemaster |
| srtsellTrdVol | number\(11\) | 공매도거래량 | 공매도거래량\(주식수, 전일기준\) | ~/shortsell,~/selectivemaster |
| srtsellTrdAmt | number\(11\) | 공매도거래금액 | 공매도거래금액\(주식수, 전일기준\) | ~/shortsell,~/selectivemaster |
| lendBalQty | number\(11\) | 대차잔고수량 | 대차잔고수량\(주식수, 전일기준\) | ~/shortsell,~/selectivemaster |
| lendBalAmt | number\(11\) | 대차잔고금액 | 단위 1,000 원 | ~/shortsell,~/selectivemaster |
| srtsellOverheatDd | number\(8\) | 공매도과열종목지정일 | 공매도 과열종목일 경우 값을 가짐 | ~/selectivemaster 요구형만 제공 |
| dd3AvgPrc | number\(11\) | 전일가격3일이동평균 | 개별종목 | ~/selectivemaster 요구형만 제공 |
| dd5AvgPrc | number\(11\) | 전일가격5일이동평균 | 개별종목, 지수 | ~/selectivemaster 요구형만 제공 |
| dd10AvgPrc | number\(11\) | 전일가격10일이동평균 | 개별종목, 지수 | ~/selectivemaster 요구형만 제공 |
| dd20AvgPrc | number\(11\) | 전일가격20일이동평균 | 개별종목, 지수 | ~/selectivemaster 요구형만 제공 |
| dd40AvgPrc | number\(11\) | 전일가격40일이동평균 | 개별종목 | ~/selectivemaster 요구형만 제공 |
| dd60AvgPrc | number\(11\) | 전일가격60일이동평균 | 개별종목, 지수 | ~/selectivemaster 요구형만 제공 |
| dd120AvgPrc | number\(11\) | 전일가격120일이동평균 | 개별종목, 지수 | ~/selectivemaster 요구형만 제공 |
| dd250AvgPrc | number\(11\) | 전일가격250일이동평균 | 개별종목 | ~/selectivemaster 요구형만 제공 |
| dd3AvgTrdVol | number\(11\) | 전일거래량3일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd5AvgTrdVol | number\(11\) | 전일거래량5일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd10AvgTrdVol | number\(11\) | 전일거래량10일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd20AvgTrdVol | number\(11\) | 전일거래량20일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd40AvgTrdVol | number\(11\) | 전일거래량40일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd60AvgTrdVol | number\(11\) | 전일거래량60일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd120AvgTrdVol | number\(11\) | 전일거래량120일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd250AvgTrdVol | number\(11\) | 전일거래량250일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd3AvgTrdAmt | number\(11\) | 전일거래대금3일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd5AvgTrdAmt | number\(11\) | 전일거래대금5일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd10AvgTrdAmt | number\(11\) | 전일거래대금10일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd20AvgTrdAmt | number\(11\) | 전일거래대금20일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd40AvgTrdAmt | number\(11\) | 전일거래대금40일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd60AvgTrdAmt | number\(11\) | 전일거래대금60일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd120AvgTrdAmt | number\(11\) | 전일거래대금120일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd250AvgTrdAmt | number\(11\) | 전일거래대금250일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd5AvgDp | number\(11\) | 전일이격도5일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd20AvgDp | number\(11\) | 전일이격도20일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd60AvgDp | number\(11\) | 전일이격도60일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| dd120AvgDp | number\(11\) | 전일이격도120일이동평균 |  | ~/selectivemaster 요구형만 제공 |
| BzDd | number\(11\) | 영업일 | 시장별 최종가동일, 입회일\(오늘일 경우 정상시장 가동\) | ~/selectivemaster 요구형만 제공 |
| IsuEngNm | string\(80\) | 종목명\(영문\) |  | ~/selectivemaster 요구형만 제공 |





## 실시간

> 요구형항목\(시장별\) -  실시간데이터

실시간으로 제공하는 요구형 데이타 주식/선물/옵션에 대해서 시장별로 정의된 항목을 제공한다.

호가, 체결 preset 으로 제공하는 데이타 항목을 요구형 실시간 데이타 항목으로 제공한다.  
아래 항목 이외의 항목에 대해서 요구형 실시간을 요청하면 ERROR를 수신하며, 실시간 요청등록은 실패한다. 

{% hint style="warning" %}
실시간시세\(요구형항목\) 서비스는 추후 제공 예정입니다.
{% endhint %}



### 주식

> 실시간 주식

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | string\(9\) | 종목단축코드 | 마스터 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 체결 |
| askStep1BstordPrc | number\(11\) | 매도1단계우선호가가격 | 호가 |
| bidStep1BstordPrc | number\(11\) | 매수1단계우선호가가격 | 호가 |
| askStep1BstordRqty | number\(12\) | 매도1단계우선호가잔량 | 호가 |
| bidStep1BstordRqty | number\(12\) | 매1단계우선호가잔량 | 호가 |
| askStep2BstordPrc | number\(11\) | 매도2단계우선호가가격 | 호가 |
| bidStep2BstordPrc | number\(11\) | 매수2단계우선호가가격 | 호가 |
| askStep2BstordRqty | number\(12\) | 매도2단계우선호가잔량 | 호가 |
| bidStep2BstordRqty | number\(12\) | 매수2단계우선호가잔량 | 호가 |
| askStep3BstordPrc | number\(11\) | 매도3단계우선호가가격 | 호가 |
| bidStep3BstordPrc | number\(11\) | 매수3단계우선호가가격 | 호가 |
| askStep3BstordRqty | number\(12\) | 매도3단계우선호가잔량 | 호가 |
| bidStep3BstordRqty | number\(12\) | 매수3단계우선호가잔량 | 호가 |
| askStep4BstordPrc | number\(11\) | 매도4단계우선호가가격 | 호가 |
| bidStep4BstordPrc | number\(11\) | 매수4단계우선호가가격 | 호가 |
| askStep4BstordRqty | number\(12\) | 매도4단계우선호가잔량 | 호가 |
| bidStep4BstordRqty | number\(12\) | 매수4단계우선호가잔량 | 호가 |
| askStep5BstordPrc | number\(11\) | 매도5단계우선호가가격 | 호가 |
| bidStep5BstordPrc | number\(11\) | 매수5단계우선호가가격 | 호가 |
| askStep5BstordRqty | number\(12\) | 매도5단계우선호가잔량 | 호가 |
| bidStep5BstordRqty | number\(12\) | 매수5단계우선호가잔량 | 호가 |
| askStep6BstordPrc | number\(11\) | 매도6단계우선호가가격 | 호가 |
| bidStep6BstordPrc | number\(11\) | 매수6단계우선호가가격 | 호가 |
| askStep6BstordRqty | number\(12\) | 매도6단계우선호가잔량 | 호가 |
| bidStep6BstordRqty | number\(12\) | 매수6단계우선호가잔량 | 호가 |
| askStep7BstordPrc | number\(11\) | 매도7단계우선호가가격 | 호가 |
| bidStep7BstordPrc | number\(11\) | 매수7단계우선호가가격 | 호가 |
| askStep7BstordRqty | number\(12\) | 매도7단계우선호가잔량 | 호가 |
| bidStep7BstordRqty | number\(12\) | 매수7단계우선호가잔량 | 호가 |
| askStep8BstordPrc | number\(11\) | 매도8단계우선호가가격 | 호가 |
| bidStep8BstordPrc | number\(11\) | 매수8단계우선호가가격 | 호가 |
| askStep8BstordRqty | number\(12\) | 매도8단계우선호가잔량 | 호가 |
| bidStep8BstordRqty | number\(12\) | 매수8단계우선호가잔량 | 호가 |
| askStep9BstordPrc | number\(11\) | 매도9단계우선호가가격 | 호가 |
| bidStep9BstordPrc | number\(11\) | 매수9단계우선호가가격 | 호가 |
| askStep9BstordRqty | number\(12\) | 매도9단계우선호가잔량 | 호가 |
| bidStep9BstordRqty | number\(12\) | 매수9단계우선호가잔량 | 호가 |
| askStep10BstordPrc | number\(11\) | 매도10단계우선호가가격 | 호가 |
| bidStep10BstordPrc | number\(11\) | 매수10단계우선호가가격 | 호가 |
| askStep10BstordRqty | number\(12\) | 매도10단계우선호가잔량 | 호가 |
| bidStep10BstordRqty | number\(12\) | 매수10단계우선호가잔량 | 호가 |
| askordTotRqty | number\(12\) | 매도호가총잔량 | 호가 |
| bidordTotRqty | number\(12\) | 매수호가총잔량 | 호가 |
| pstoffhrAskTotOrdRqty | number\(15\) | 장종료후시간외매도총호가잔량 | 호가 |
| pstoffhrBidTotOrdRqty | number\(15\) | 장종료후시간외매수총호가잔량 | 호가 |
| deemTrdPrc | number\(11\) | 예상체결가격 | 체결 |
| deemTrdvol | number\(12\) | 예상체결수량 | 체결 |
| deemAccTrdvol | number\(12\) | 예상누적체결수량 | 체결 |
| cmpprevddTpCd | string\(1\) | 전일대비구분코드 | 체결 |
| cmpprevddPrc | number\(11\) | 전일대비가격 | 체결 |
| trdPrc | number\(11\) | 체결가격 | 체결 |
| trdvol | number\(10\) | 상장중최저가일자 | 체결 |
| opnprc | number\(11\) | 시가 | 체결 |
| hgprc | number\(11\) | 고가 | 체결 |
| lwprc | number\(11\) | 저가 | 체결 |
| accTrdval | number\(22\) | 누적거래대금 | 체결 |
| lstAskbidTpCd | string\(1\) | 최종매도매수구분코드 | 체결 |
| trdTm | string\(8\) | 체결시각,거래시각 | 체결 |



### 선물

> 실시간 선물

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | string\(12\) | 종목단축코드 | 마스터 |
| bidTotOrdRqty | number\(12\) | 매수총호가잔량 | 호가 |
| bidStep1BstordPrc | number\(11\) | 매수1단계우선호가가격 | 호가 |
| bidStep1BstordRqty | number\(12\) | 매수1단계우선호가잔량 | 호가 |
| bidStep2BstordPrc | number\(11\) | 매수2단계우선호가가격 | 호가 |
| bidStep2BstordRqty | number\(12\) | 매수2단계우선호가잔량 | 호가 |
| bidStep3BstordPrc | number\(11\) | 매수3단계우선호가가격 | 호가 |
| bidStep3BstordRqty | number\(12\) | 매수3단계우선호가잔량 | 호가 |
| bidStep4BstordPrc | number\(11\) | 매수4단계우선호가가격 | 호가 |
| bidStep4BstordRqty | number\(12\) | 매수4단계우선호가잔량 | 호가 |
| bidStep5BstordPrc | number\(11\) | 매수5단계우선호가가격 | 호가 |
| bidStep5BstordRqty | number\(12\) | 매수5단계우선호가잔량 | 호가 |
| askTotOrdRqty | number\(12\) | 매도총호가잔량 | 호가 |
| askStep1BstordPrc | number\(11\) | 매도1단계우선호가가격 | 호가 |
| askStep1BstordRqty | number\(12\) | 매도1단계우선호가잔량 | 호가 |
| askStep2BstordPrc | number\(11\) | 매도2단계우선호가가격 | 호가 |
| askStep2BstordRqty | number\(12\) | 매도2단계우선호가잔량 | 호가 |
| askStep3BstordPrc | number\(11\) | 매도3단계우선호가가격 | 호가 |
| askStep3BstordRqty | number\(12\) | 매도3단계우선호가잔량 | 호가 |
| askStep4BstordPrc | number\(11\) | 매도4단계우선호가가격 | 호가 |
| askStep4BstordRqty | number\(12\) | 매도4단계우선호가잔량 | 호가 |
| askStep5BstordPrc | number\(11\) | 매도5단계우선호가가격 | 호가 |
| askStep5BstordRqty | number\(12\) | 매도5단계우선호가잔량 | 호가 |
| bidValidOrdCnt | number\(11\) | 매수유효호가건수 | 호가 |
| bidStep1BstordCnt | number\(11\) | 매수1단계우선호가건수 | 호가 |
| bidStep2BstordCnt | number\(11\) | 매수2단계우선호가건수 | 호가 |
| bidStep3BstordCnt | number\(11\) | 매수3단계우선호가건수 | 호가 |
| bidStep4BstordCnt | number\(11\) | 매수4단계우선호가건수 | 호가 |
| bidStep5BstordCnt | number\(11\) | 매수5단계우선호가건수 | 호가 |
| askValidOrdCnt | number\(11\) | 매도유효호가건수 | 호가 |
| askStep1BstordCnt | number\(11\) | 매도1단계우선호가건수 | 호가 |
| askStep2BstordCnt | number\(11\) | 매도2단계우선호가건수 | 호가 |
| askStep3BstordCnt | number\(11\) | 매도3단계우선호가건수 | 호가 |
| askStep4BstordCnt | number\(11\) | 매도4단계우선호가건수 | 호가 |
| askStep5BstordCnt | number\(11\) | 매도5단계우선호가건수 | 호가 |
| ordAcptTm | string\(11\) | 호가접수시각 | 호가 |
| deemTrdPrc | number\(11\) | 예상체결가격 | 체결 |
| trdPrc | number\(11\) | 체결가격 | 체결 |
| trdvol | number\(10\) | 체결수량,거래량 | 체결 |
| trdTm | string\(8\) | 체결시각,거래시각 | 체결 |
| fstmmAgndaContrtPrc | number\(11\) | 최근월물의제약정가격 | 체결 |
| futrmmAgndaContrtPrc | number\(11\) | 원월물의제약정가격 | 체결 |
| opnprc | number\(11\) | 시가 | 체결 |
| hgprc | number\(11\) | 고가 | 체결 |
| lwprc | number\(11\) | 저가 | 체결 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 체결 |
| accTrdval | number\(22\) | 누적거래대금 | 체결 |
| negoBlkAccTrdvol | number\(12\) | 협의대량누적체결수량 | 체결 |
| lstTrdTpCd | string\(1\) | 최종매도매수구분코드 | 체결 |
| realtmUplmtprc | number\(11\) | 실시간상한가 | 체결 |
| realtmLwlmtprc | number\(11\) | 실시간하한가 | 체결 |



### 옵션 

> 실시간 옵션

| **Name** | **Type** | **Description** |  |
| :--- | :--- | :--- | :--- |
| isuSrtCd | string\(12\) | 종목단축코드 | 마스터 |
| bidTotOrdRqty | number\(12\) | 매수총호가잔량 | 호가 |
| bidStep1BstordPrc | number\(11\) | 매수1단계우선호가가격 | 호가 |
| bidStep1BstordRqty | number\(12\) | 매수1단계우선호가잔량 | 호가 |
| bidStep2BstordPrc | number\(11\) | 매수2단계우선호가가격 | 호가 |
| bidStep2BstordRqty | number\(12\) | 매수2단계우선호가잔량 | 호가 |
| bidStep3BstordPrc | number\(11\) | 매수3단계우선호가가격 | 호가 |
| bidStep3BstordRqty | number\(12\) | 매수3단계우선호가잔량 | 호가 |
| bidStep4BstordPrc | number\(11\) | 매수4단계우선호가가격 | 호가 |
| bidStep4BstordRqty | number\(12\) | 매수4단계우선호가잔량 | 호가 |
| bidStep5BstordPrc | number\(11\) | 매수5단계우선호가가격 | 호가 |
| bidStep5BstordRqty | number\(12\) | 매수5단계우선호가잔량 | 호가 |
| askTotOrdRqty | number\(12\) | 매도총호가잔량 | 호가 |
| askStep1BstordPrc | number\(11\) | 매도1단계우선호가가격 | 호가 |
| askStep1BstordRqty | number\(12\) | 매도1단계우선호가잔량 | 호가 |
| askStep2BstordPrc | number\(11\) | 매도2단계우선호가가격 | 호가 |
| askStep2BstordRqty | number\(12\) | 매도2단계우선호가잔량 | 호가 |
| askStep3BstordPrc | number\(11\) | 매도3단계우선호가가격 | 호가 |
| askStep3BstordRqty | number\(12\) | 매도3단계우선호가잔량 | 호가 |
| askStep4BstordPrc | number\(11\) | 매도4단계우선호가가격 | 호가 |
| askStep4BstordRqty | number\(12\) | 매도4단계우선호가잔량 | 호가 |
| askStep5BstordPrc | number\(11\) | 매도5단계우선호가가격 | 호가 |
| askStep5BstordRqty | number\(12\) | 매도5단계우선호가잔량 | 호가 |
| bidValidOrdCnt | number\(11\) | 매수유효호가건수 | 호가 |
| bidStep1BstordCnt | number\(11\) | 매수1단계우선호가건수 | 호가 |
| bidStep2BstordCnt | number\(11\) | 매수2단계우선호가건수 | 호가 |
| bidStep3BstordCnt | number\(11\) | 매수3단계우선호가건수 | 호가 |
| bidStep4BstordCnt | number\(11\) | 매수4단계우선호가건수 | 호가 |
| bidStep5BstordCnt | number\(11\) | 매수5단계우선호가건수 | 호가 |
| askValidOrdCnt | number\(11\) | 매도유효호가건수 | 호가 |
| askStep1BstordCnt | number\(11\) | 매도1단계우선호가건수 | 호가 |
| askStep2BstordCnt | number\(11\) | 매도2단계우선호가건수 | 호가 |
| askStep3BstordCnt | number\(11\) | 매도3단계우선호가건수 | 호가 |
| askStep4BstordCnt | number\(11\) | 매도4단계우선호가건수 | 호가 |
| askStep5BstordCnt | number\(11\) | 매도5단계우선호가건수 | 호가 |
| ordAcptTm | string\(11\) | 호가접수시각 | 호가 |
| deemTrdPrc | number\(11\) | 예상체결가격 | 체결 |
| trdPrc | number\(11\) | 체결가격 | 체결 |
| trdvol | number\(10\) | 체결수량,거래량 | 체결 |
| trdTm | string\(8\) | 체결시각,거래시각 | 체결 |
| opnprc | number\(11\) | 시가 | 체결 |
| hgprc | number\(11\) | 고가 | 체결 |
| lwprc | number\(11\) | 저가 | 체결 |
| accTrdvol | number\(12\) | 누적체결수량,누적거래량 | 체결 |
| accTrdval | number\(22\) | 누적거래대금 | 체결 |
| negoBlkAccTrdvol | number\(12\) | 협의대량누적체결수량 | 체결 |
| lstTrdTpCd | string\(1\) | 최종매도매수구분코드 | 체결 |
| realtmUplmtprc | number\(11\) | 실시간상한가 | 체결 |
| realtmLwlmtprc | number\(11\) | 실시간하한가 | 체결 |





