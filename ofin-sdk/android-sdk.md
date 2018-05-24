---
description: Fintech Mobile SDK Guide - Android
---

# android sdk

## 개요

O'FIN\(오핀\)은 금융투자회사, 유관기관, 핀테크 기업의 데이터와 서비스를 Open API로 게시하고, 상호 융합을 통해 혁신적 비즈니스를 만들 수 있도록 하는 핀테크 오픈 플랫폼입니다. 

본 문서는 API 호출 시 사용자 인증 및 권한을 부여하여 안전하고 표준화된 방법으로 서비스를 제공하기 위한 ‘오핀’ 앱 연동 Oppflib \(SDK\) 사용 설명서입니다.



## 전체 진행 시나리

![Android &#xC2DC;&#xB098;&#xB9AC;&#xC624;](../.gitbook/assets/image%20%2813%29.png)



## 준비 사항

**Library File Import**

라이브러리 사용을 위해 Android Studio/Eclipse 에 배포된 라이브러리 \(oppflib.jar\)를 추가합니다.

Project &gt; Open Module Settings &gt; Dependencies &gt; \(+\)  add File dependency &gt; oppflib.jar 추가

![Library Import](../.gitbook/assets/image%20%2866%29.png)



## 연동

### Activity 설정

Koscom SDK를 연동하기 위해서는 OPPFLibAppActivity, OPPFLibFragmentActivity 또는 OPPFLibAppCompatActivity를 상속받아 구현 해야 합니다. 응답 결과는 OPPFLibFintech.FintechListener를 통해서 전달받을 수 있습니다.

```java
// JoinActivity.java SDK를 호출하는 코드를 가지고 있는 Activity 파일

import com.oppf.mobile.lib.OPPFLibAppCompatActivity;
import com.oppf.mobile.lib.OPPFLibFintech;
import com.oppf.mobile.lib.OPPFLibParameterException;

public class JoinActivity extends OPPFLibAppCompatActivity {

    private OPPFLibFintech fintech = null;  //OPPFLibFintech 객체를 변수로 선언

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_join);      

        fintech = new OPPFLibFintech(); //변수 초기화
    }
```



### SDK 호출

SDK 를 호출하는 방법으로  requestForResult 방식과 requestForActivityResult 방식  두 가지를 제공합니다.

  
**1. OPPFLibFintech\#requestForResult** 를 이용하는 경우

Activity에 응답 수신용 Custom URL Schem과 launchMode를 "singleTask"으로설정  
URL Scheme :”scheme://host” \(ex.   “fintech-app://com.example.kscomapisdk.join" \)

> AndroidManifest launchMode, URL Scheme 설정

```java
// AndroidManifest.xml 파일 설정 예
<activity
   android:name=".JoinActivity"
   android:label="@string/app_name"
   android:launchMode="singleTask">
   <intent-filter>
       <action android:name="android.intent.action.VIEW" />
       <category android:name="android.intent.category.DEFAULT" />
       <category android:name="android.intent.category.BROWSABLE" />
       <data android:scheme="fintech-app" android:host="com.fintech.oppf2.app.join" />
   </intent-filter>
</activity>
```

> requestForResult 를 사용하여 SDK를 호출

```java
/*
* Koscom Open API App 샐행. Activity의 startActivity를 호출.
* 응답 결과 수신을 위해 Fintech-App에 Custom URL Schem를 설정하고 전달해야함.
*/
private void startJoinSampleForActivity() {
    JSONObject data = new JSONObject();
    /*
     * Koscom Open API App 샐행 <br>
     * Custom URL Schem으로 Intent를 구성하여 Activity의 startActivity를 호출하여 <br>
     * Koscom Open API App을 실행하고 응답 결과는 Fintech-App에 Custom URL Schem를 설정하고 <br>
     * 서비스 호출 시 데이터와 같이 전달하여 수신한다.
     *
     * @param activity OPPFLibAppCompatActivity, Activity는 OPPFLibAppCompatActivity 상속 받아 구현하여야 한다.
     * @param fn String, Koscom Open API의 서비스 이름
     * @param data JSONObject, App에 전달 할 데이터
     * @param callbackUrl String, 응답 수신용 Custom URL Schem
     * @param listener OPPFLibFintech.FintechListener, Koscom Open API 응답 수신 리스너
    */
    try {
      fintech.requestForResult((OPPFLibAppCompatActivity)this, 
    		“join", 
    		data, 
    		"fintech-app://com.fintech.oppf2.app.join", 
    		new ExFintechListener());
  
      } catch (ActivityNotFoundException e) {
        e.printStackTrace();
        showResultDialog("FinTech 회원가입 결과", "서비스 연동 실패[join] " + e.getLocalizedMessage());
  
      } catch (OPPFLibParameterException e) {
        e.printStackTrace();
        showResultDialog("FinTech 회원가입 결과", "서비스 연동 실패[join] " + e.getLocalizedMessage());
    }
}
```

  
**2. OPPFLibFintech\#requestForActivityResult** 를 사용하여 SDK를 호출

Custom URL Schem과 launchMode를 설정 할 필요가 없다.

```java
/**
* Koscom Open API App 샐행. Activity의 startActivityForResult를 호출
*/
private void startJoinSampleForActivityResult() {
    // API로 전달할 data를 JSONObject 로 생성하여 전달
    JSONObject data = new JSONObject();
    /*
     * Koscom Open API App 샐행 <br>
     * CustomURL Schem으로 Intent를 구성하여 Activity의 startActivityForResult를 호출하여 <br>
     * Koscom Open API App을 실행하고 응답 결과는 OPPFLibAppCompatActivity의 onActivityResult를 통해 전달 받는다. <br>
     *
     * @param activity OPPFLibAppCompatActivity, Activity는 OPPFLibAppCompatActivity를 상속 받아 구현하여야 한다.
     * @param fn String, Koscom Open API의 서비스 이름
     * @param data JSONObject, App에 전달 할 데이터
     * @param listener OPPFLibFintech.FintechListener, Koscom Open API 응답 수신 리스너
     */
      try {
            fintech.requestForActivityResult((OPPFLibAppCompatActivity)this, 
					"join", 
					data,
					new ExFintechListener());
								
      } catch (ActivityNotFoundException e) {
          e.printStackTrace();
          showResultDialog("FinTech 회원가입 결과", "서비스 연동 실패[join] " + e.getLocalizedMessage());

      } catch (OPPFLibParameterException e) {
          e.printStackTrace();
          showResultDialog("FinTech 회원가입 결과", "서비스 연동 실패[join] " + e.getLocalizedMessage());
      }
}
```



### 응답

**응답 결과 받는 소스 코드**

```java
// OPPFLibFintech.FintechListener 를 상속 받아 응답 처리 하는 소스 코드  
/**
* Koscom Open API 응답 결과를 전달 받기 위한 인터페이스 구현 클래스
* @see com.oppf.mobile.lib.OPPFLibFintech.FintechListener
*
*/
private class ExFintechListener implements OPPFLibFintech.FintechListener {
    
    /**
     * 서비스 요청 성공 시 서비스 응답 결과를 전달 빋기 위한 인터페이스
     * @param fn String, Koscom Open API의 서비스 이름
     * @param message String, 응답  message
     * @param data JSONObject, 응답 데이터
     */
     @Override
     public void onKoscomResultData(String fn, String message, JSONObject data) {
         showResultDialog("FinTech 회원가입 결과", message + "\n" + data.toString());
     }
     
     /**
      * 서비스 요청 실패를 전달 빋기 위한 인터페이스
      * @param fn String, Koscom Open API의 서비스 이름
      * @param code String, 응답  code
      * @param message String, 응답 message
      */
     @Override
     public void onKoscomResultFail(String fn, String code, String message) {
         showResultDialog("FinTech 회원가입 결과", "서비스 연동 실패[" + fn + "] code[" + code+ "] " + message);
     }
}
```

**응답 결과 코드**

CODE\_SUCCESS                           =   2000 ;  
CODE\_CANCEL                             =   -1 ;  
CODE\_FAIL\_FINTECH\_REJECT  =   "4001" ;



### API서비스 정보

fn 은 해당 업무에 대한 키값 입니다.    
data 필드는 해당 업무에 필요한 데이터를 정의 합니다. 각 업무에 필요한 값들을 json object로 전달 합니다.	

#### **1.  회원 가입 API 호출 \( fn : join \)**

서비스 연동 API의 ‘오핀’ – ‘회원가입 여부를 확인’ 후 결과가 ‘nonmember’인 경우 ‘오핀’ 의 회원가입 페이지 호출

```java
/**
* Koscom Open API App 샐행. Activity의 startActivityForResult를 호출
*/
private void startJoinSampleForActivityResult() {
    // API로 전달할 data를 JSONObject 로 생성하여 전달
	JSONObject data = new JSONObject();
    
    /*
     * Koscom Open API App 샐행 <br>
     * CustomURL Schem으로 Intent를 구성하여 Activity의 startActivityForResult를 호출하여 <br>
     * Koscom Open API App을 실행하고 응답 결과는 OPPFLibAppCompatActivity의 onActivityResult를 통해 전달 받는다. <br>
     *
     * @param activity OPPFLibAppCompatActivity, Activity는 OPPFLibAppCompatActivity를 상속 받아 구현하여야 한다.
     * @param fn String, Koscom Open API의 서비스 이름
     * @param data JSONObject, App에 전달 할 데이터
     * @param listener OPPFLibFintech.FintechListener, Koscom Open API 응답 수신 리스너
     */
      try {
          fintech.requestForActivityResult((OPPFLibAppCompatActivity)this,
				"join",
				data, 
				new ExFintechListener());
				
      } catch (ActivityNotFoundException e) {
          e.printStackTrace();
          showResultDialog("FinTech 회원가입 결과", "서비스 연동 실패[join] " + e.getLocalizedMessage());

       } catch (OPPFLibParameterException e) {
          e.printStackTrace();
          showResultDialog("FinTech 회원가입 결과", "서비스 연동 실패[join] " + e.getLocalizedMessage());
      }
}
```



