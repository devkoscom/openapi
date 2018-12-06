# Android

## 개요

O'FIN\(오핀\)은 금융투자회사, 유관기관, 핀테크 기업의 데이터와 서비스를 Open API로 게시하고, 상호 융합을 통해 혁신적 비즈니스를 만들 수 있도록 하는 핀테크 오픈 플랫폼입니다. 

본 문서는 API 호출 시 사용자 인증 및 권한을 부여하여 안전하고 표준화된 방법으로 서비스를 제공하기 위한 ‘오핀’ 앱 연동 Oppflib \(SDK\) 사용 설명서입니다.



## 전체 진행 시나리오

![OFin &#xC2DC;&#xB098;&#xB9AC;&#xC624;](../.gitbook/assets/image%20%2817%29.png)



## 준비 사항

**Library File Import**

라이브러리 사용을 위해 Android Studio/Eclipse 에 배포된 라이브러리 \(oppflib.jar\)를 추가합니다.

Project &gt; Open Module Settings &gt; Dependencies &gt; \(+\)  add File dependency &gt; oppflib.jar 추가

![Library Import](../.gitbook/assets/image%20%2885%29.png)





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

  
**1.  OPPFLibFintech\#requestForResult** 를 이용하는 경우

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

  
**2.  OPPFLibFintech\#requestForActivityResult** 를 사용하여 SDK를 호출

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



\*  **회원가입 페이지로 이동**

회원가입 안내  
회원가입 API 호출이 성공하면, 가입에 대한 안내 화면으로 이동합니다. 내용 확인 후 \[가입진행\] 버튼을 터치합니다.

![&#xD68C;&#xC6D0;&#xAC00;&#xC785; &#xC548;&#xB0B4;](../.gitbook/assets/image%20%2862%29.png)

약관 및 본인인증  
약관에 동의하시면 휴대폰 인증 버튼이 활성화됩니다. 

![&#xC57D;&#xAD00; &#xBC0F; &#xBCF8;&#xC778;&#xC778;&#xC99D;](../.gitbook/assets/image%20%2897%29.png)

휴대폰 인증  
정보 입력 후 \[인증번호 전송\] 버튼을 터치하면 SMS로 인증번호가 발송됩니다. 수신된 인증번호 입력 후 \[인증하기\] 버튼을 터치합니다. 

![&#xD734;&#xB300;&#xD3F0; &#xC778;&#xC99D;](../.gitbook/assets/image%20%2887%29.png)



**2.  OAuth 로그인창 API 호출 \( fn : oauth \)**

‘오핀’의 OAuth로그인을 통해 사용자 인증을 요청 합니다.   
responseType 은 안전한 금융거래 정보 보호를 위해 ‘Authorization Code’ 방식만 제공 합니다. 입력 파라메터는 ‘Authorization Code 요청’ 과 동일하며, callbackUrl로 Code값을 전달 합니다. Access token 은 기존 절차에 따릅니다. 

{% hint style="info" %}
OAuth 절차는 [이곳](https://koscom.gitbook.io/open-api/authentication/oauth) 을 참조하세요.
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="JSON 파라미터 예제" %}
```yaml
{
  "data": {
      "scope": "account",
      "callbackUrl": "https://open.koscom.co.kr/CallbackURL",
      "clientId": "l7xx296eb0af278542b38a6ebd507xxxxxxx",
      "responseType": "code",
      "state": "test"
   }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

해당 API는 사용자 인증을 위한 OAuth 로그인창만 제공하며, Access Token 취득은 기존 URL을 통해 획득 하시면 됩니다. 인증 성공 \(SUCCESS\), 인증 실패\(FAIL\)는 아래와 같은 에러가 리턴 됩니다.   
더 자세한 에러 코드 정보는 [이곳](https://koscom.gitbook.io/open-api/error-code#oauth-error) 에서 확인하세요.

> OAuth 로그인창 Error Code

| **`Error code`** | **`Description`** |
| :--- | :--- |
| 4000 | 일반적인 에러 |
| 4100 | API 및 서비스 이용 권한 획득에 실패한 경우. |
| 4200 | Authorization Code 전달에 실패한 경우 |
| 4300 | 사용자가 요청한 리소스의 권한 허용 거부 |
| 4400 | 비회원 인증 중 이미 가입된 회원 |

{% code-tabs %}
{% code-tabs-item title="Service OAuth API Request Example" %}
```java
/**
* Koscom Open API App 샐행. Activity의 startActivity를 호출.
* 응답 결과 수신을 위해 Fintech-App에 Custom URL Schem를 설정하고 전달해야함.
*/
private void startOAuthSampleForActivity() {
    JSONObject data = new JSONObject();
    try {
        EditText editText = (EditText) this.findViewById(R.id.input_scope);
        data.put("scope", editText.getText().toString());
        EditText editText1 = (EditText) this.findViewById(R.id.input_url);
        data.put("callbackUrl", editText1.getText().toString());
        EditText editText2 = (EditText) this.findViewById(R.id.input_cliId);
        data.put("clientId", editText2.getText().toString());
        EditText editText3 = (EditText) this.findViewById(R.id.input_respType);
        data.put("responseType", editText3.getText().toString());
        EditText editText4 = (EditText) this.findViewById(R.id.input_state);
        data.put("state", editText4.getText().toString());
    
    } catch (JSONException e) {
        e.printStackTrace();
    }
    
    /*
     * Koscom Open API App 샐행 <br>
     * Custom URL Schem으로 Intent를 구성하여 Activity의 startActivity를 호출하여 <br>
     * Koscom Open API App을 실행하고 응답 결과는 Fintech-App에 Custom URL Schem를 설정하고 <br>
     * 서비스 호출 시 데이터와 같이 전달하여 수신한다.
     *
     * @param activity OPPFLibActivity, Activity는 OPPFLibActivity를 상속 받아 구현하여야 한다.
     * @param fn String, Koscom Open API의 서비스 이름
     * @param data JSONObject, App에 전달 할 데이터
     * @param callbackUrl String, 응답 수신용 Custom URL Schem
     * @param listener OOPPFLibFintech.FintechListener, Koscom Open API 응답 수신 리스너
    */
    try {
        fintech.requestForResult((OPPFLibActivity)this, "oauth", data, "fintech-app://com.fintech.oppf2.app.oauth", new ExFintechListener());
    
    } catch (ActivityNotFoundException e) {
        e.printStackTrace();
        showResultDialog("FinTech OAuth 결과", "서비스 연동 실패[oauth] " + e.getLocalizedMessage());
    
    } catch (OPPFLibParameterException e) {
        e.printStackTrace();    
        showResultDialog("FinTech OAuth 결과", "서비스 연동 실패[oauth] " + e.getLocalizedMessage());
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}



 **\*  OAuth 로그인창 호출**

OAuth 로그인  
OAuth  로그인창 호출시 , OFIN설치 여부 체크 후 설치되어 있을 경우 OFIN 실행&gt;OAuth 화면이 열립니다. 

![OAuth &#xB85C;&#xADF8;&#xC778;](../.gitbook/assets/image%20%2828%29.png)

정보제공 권한 허용  
OAuth로그인이 완료되면 정보제공 권한 여부 설정 화면으로 이동합니다. \[허용\] 터치 시 핀테크 앱의 서비스를 이용할 수 있습니다. 

![&#xC815;&#xBCF4;&#xC81C;&#xACF5; &#xAD8C;&#xD55C; &#xD5C8;&#xC6A9;](../.gitbook/assets/image%20%28120%29.png)



**3.  앱 상세 페이지 이동 API 호출 \( fn : appRequest \)**

서비스연동 API \(가상계좌 리스트 조회\) 확인 후 해당 고객에 연결된 계좌가 없거나 추가로 앱 사용 신청이 필요한 경우 ‘오핀’ 앱 상세 페이지로 이동하여 서비스 신청을 유도 합니다.  
\* appId : 앱 등록 후 할당 받은 AppID 값을 입력

{% code-tabs %}
{% code-tabs-item title="JSON parameter Example" %}
```yaml
{
   "data": {
      "appId": "139"
   }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="앱 상세페이지 이동 API 호출 Example" %}
```java
private void startRequestSampleForActivityResult() {
    JSONObject data = new JSONObject();
    try {
        data.put("appId", this.findViewById(R.id.input_appId));
    
    } catch (JSONException e) {
        e.printStackTrace();
    }
    
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
        fintech.requestForActivityResult((OPPFLibAppCompatActivity)this, "appRequest", data, new ExFintechListener());
    
    } catch (ActivityNotFoundException e) {
        e.printStackTrace();
        showResultDialog("FinTech App 신청 결과", "서비스 연동 실패[request] " + e.getLocalizedMessage());
    
    } catch (OPPFLibParameterException e) {
        e.printStackTrace();
        showResultDialog("FinTech App 신청 결과", "서비스 연동 실패[request] " + e.getLocalizedMessage());
    }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}



 **\*  앱 상세 페이지로 이동**

앱 소개 \(상세\)  
앱 상세 페이지로 이동 및 사용 신청을 유도 합니다. 

![](../.gitbook/assets/image%20%2891%29.png)

연결계좌 선택  
가상계좌를 발급 및 연결 계좌를 선택 합니다. 

![](../.gitbook/assets/image%20%2890%29.png)

앱 사용 신청 완료  
사용 신청이 정상적으로 완료 되면 해당 핀테크 서비스를 사용 하실 수 있습니다. 

![](../.gitbook/assets/image%20%2896%29.png)





## API Reference

### 

### OPPFLibActivity / OPPFLibFragmentActivity / OPPFLibAppCompatActivity

SDK 를 사용하기 위하여 Activity 파일에서 상속해야 하는 Activity Class 입니다. OPPFLibActivity 는 Activity를 상속하고, OPPFLibFragmentActivity 는 FragmentActivity 를 상속하며, OPPFLibAppCompatActivity 는 AppCompatActivity 를 상속합니다. \(상황에 맞게 사용하시면 됩니다. 

  
**setURLSchemeListener**

| **Syntax** | void setURLSchemeListener\(OPPFLibURLSchemeListener urlSchemeListener\) |
| :--- | :--- |
| **Parameter** | OPPFLibURLSchemeListener urlSchemeListener  _- 서비스 결과를 전달 받기 위한 인터페이스\(OPPFLibURLSchemeListener\) 객체_ |
| **Description** | Koscom Open API App에서 전달 빋은 서비스 결과를 전달 받기 위한 인터페이스 객체를 등록한다. |
| **Note** | OPPFLibFintech의 requestForActivityResult / requestForResult 에서 사용 됩니다. |





### OPPFLibFintech

**requestForResult**

| **Syntax** | void requestForResult\(final OPPFLibActivity activity, final String fn, JSONObject data, String resCallbackUrl, final FintechListener listener\) |
| :--- | :--- |
| **Parameter** | OPPFLibActivity activity _- Activity는 OPPFLibActivity를 상속 받아 구현_ // String fn _- Koscom Open API의 서비스 이름_ // JSONObject data _- App에 전달 할 데이터_ // String resCallbackUrl _- 응답 수신용 Custom URL Scheme_ // final FintechListener listener _- Koscom Open API 응답 수신 리스너_ |
| **Description** | Koscom Open API App 실행하는 함수.  Custom URL Schem으로 Intent를 구성, Activity의 startActivity를 호출하여Koscom Open API App을 실행합니다. 응답 결과는 서비스 호출 시 데이터와 같이 전달한 수신합니다. |
| **Note** | OPPFLibFragmentActivity 또는 OPPFLibAppCompatActivity 를 Parameter 로 받는 동일 함수가 있습니다. |

  
**requestForActivityResult**

| **Syntax** | public void requestForActivityResult\(final OPPFLibAppCompatActivity activity, final String fn, final JSONObject data, final FintechListener listener\) |
| :--- | :--- |
| **Parameter** | OPPFLibActivity activity _- Activity는 OPPFLibActivity를 상속 받아 구현_ // String fn _- Koscom Open API의 서비스 이름_ // JSONObject data _- App에 전달 할 데이터_ // final FintechListener listener _- Koscom Open API 응답 수신 리스너_ |
| **Description** | Koscom Open API App 실행하는 함수.  Custom URL Schem으로 Intent를 구성, Activity의 startActivity를 호출하여 Koscom Open API App을 실행하고 응답 결과는 OPPFLibAppCompatActivity onActivityResult를 통해 전달 받습니다. |
| **Note** | OPPFLibFragmentActivity 또는 OPPFLibAppCompatActivity 를 Parameter 로 받는 동일 함수가 있습니다. |

  
**goAppStore**

| **Syntax** | public void goAppStore\(final Activity activity\)  |
| :--- | :--- |
| **Parameter** | Activity activity _- activity.startActivity 에 새로운 intent로 PlayStore 화면을 띄우는 방식._ |
| **Description** | PlayStore 설치 화면으로 이동한다. |





### **\(interface\) FintechListener**

Koscom Open API 응답 결과를 전달 받기 위한 인터페이스 정의 클래스

  
**onKoscomResultData**

| **Syntax** | public void goAppStore\(final Activity activity\)  |
| :--- | :--- |
| **Parameter** | String fn _- Koscom Open API의 서비스 이름_ // String message _- 응답 message_ // JSONObject data _- 응답 데이터_ |
| **Description** | 서비스 요청 성공 시 서비스 응답 결과를 전달 받기 위한 인터페이스 |

  
**onKoscomResultFail**

| **Syntax** | public void goAppStore\(final Activity activity\)  |
| :--- | :--- |
| **Parameter** | String fn _- Koscom Open API의 서비스 이름_ // String code _- 응답 error code_ // String message _- 응답 message_ // |
| **Description** | 서비스 요청 실패를 전달 받기 위한 인터페이스 |



