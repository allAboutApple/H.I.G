# **Accounts**

앱의 핵심 기능에 필요한 경우에만 사람들에게 계정을 만들도록 요청하는게 좋다. 따라서 계정 없이도 앱을 즐길 수 있도록 하는것이 좋다. 앱의 로그인 기능을 넣는다면 Apple 로그인을 사용하여 경험을 제공하자!

- **Explain the benefits of creating an account and how to sign up**
  
    앱에서 계정이 필요하다면 필요한 요구사항과 이유에 대해 간략히 설명하는 메세지를 로그인화면에 간략하게 표기하자


- **Delay sign-in for as long as possible**
  
    작업 수행 전에 강제로 로그인을 해야하는 경우 앱 사용 자체를 포기할 확률이 커진다. 쇼핑앱에서 탐색할 기회를 계속 제공하다가 구매할 타이밍에 로그인을 요구하는 식으로 하는게 좋다.
- **If you don’t use Sign in with Apple, use Password AutoFill.**
  
  암호 자동완성은 암호와 보안 코드를 자동으로 생성하고 입력하므로, 사람들이 인증 화면에서 보내는 시간을 줄일 수 있다. [개발자 가이드 바로가기!](https://developer.apple.com/documentation/security/password_autofill/)
- **Avoid using the term passcode to refer to account authentication**
  
    password, PIN, code, pass phrase, key, access code와 같은 단어의 대체용어를 고려해서 사용하자.

<br/>
<br/>

<br/>
<br/>

### **Account Deletion**

사람들이 앱 내에서 계정을 생성하도록 도우려면 계정 비활성화와 삭제도 가능하게해야한다. 
<br/>

법적으로 앱이 건강기록과 같은 계정 또는 정보를 유지관리하거나 특정 계정 삭제 프로세스를 따라야하는 경우,사람들에게 유지해야하는 정보 또는 계정과 따라야하는 프로세스를 이애할 수 있도록 알려야한다.

<br/>
<br/>

- **provide a clear way to initiate account deletion within your app**
  
  만약 사람들이 우리 앱 내에서 계정 삭제를 수행할 수 없는 경우, 계정삭제를 할 수 있는 웹 페이지 링크를 제공해야하며 그 링크를 찾기 쉽게 만들어야한다.
    - 만약 사람들이 [Sign in with Apple](https://developer.apple.com/design/human-interface-guidelines/sign-in-with-apple/overview/introduction/)을 사용하여 앱 내에서 계정을 생성한 경우, 계정을 삭제할 때 연결된 토큰을 revoke해야한다. ( [revoke token](https://developer.apple.com/documentation/sign_in_with_apple/revoke_tokens) )
        
        token을 invalidate시키고 앱에 더 이상 연관된 유저 정보를 가지고있지 않게하는 api를 call해야한다.
        
- **provide a consistent account-deletion experience whether people perform it within your app or on the website**
  
    앱에서 계정을 삭제하던, 웹에서 계정을 삭제하던지간에 두 프로세스가 같아야한다. 어떤 곳에서는 더 긴 프로세스를 가지게하거나 그런 방식이면 안된다.
- **consider letting people schedule account deletion to occur in the future.**
  
  예약 삭제를 제공할 수도 있다. (만약 예약 삭제를 제공하는 경우 즉시 삭제는 반드시 필요함)
- **tell people when account deletion will complete, and notify them when it’s finished.**
  
  계정을 삭제할 때 시간이 걸리는 경우, 삭제프로세스에대해 사람들에게 알려줘서 예상 결과를 알 수 있게 하자

- **if you support in-app purchases, help people understand how billing and cancellation work when they delete their account.**
  
    인앱구매를 지원하는 앱에서 계정 삭제시 일어나는 시나리오를 설명해야한다.
    - 자동 갱신 구독에 대한 청구는 계정 삭제와 관련없이 사용자가 애플설정에서 구독을 취소할 때 까지 계속되기대문에 따로 구독취소를 하거나 환불요청하는 프로세스를 더해야한다.
    
    이런 시나리오를 이해하도록 해야하는 의무도 있지만, 구독 취소 및 구매 관리하는 법도 앱내에서 제공해야한다. 더 자세한 가이드라인은 [구독관리](https://developer.apple.com/design/human-interface-guidelines/in-app-purchase/overview/auto-renewable-subscriptions/#helping-people-manage-their-subscriptions)와 [앱 내 구매](https://developer.apple.com/design/human-interface-guidelines/in-app-purchase/overview/introduction/#providing-help-with-in-app-purchases) 에 대한 것을 확인!
    

<br/>
<br/>
<br/>
<br/>

### **Face ID and Touch ID**

face id와 touch id는 사람들이 신뢰하는 친숙한 인증 방법이다. 앱 내에서 해당 기능을 제공하는 경우, 생체인증을 끌 때의 시나리오도 고려해야한다.

[Local Authentication에서 개발 지침 확인](https://developer.apple.com/documentation/localauthentication)

<br/>

앱 내에서 local authentication을 사용한다한들, 보안을 위해서 앱은 underlying authentication에 접근할 수 없게 설계되어있다. (즉 터치 아이디를 사용한다한들 앱에서 지문에대한 이미지를 얻을 수 없다는 것!) 

<Br/>

- **reduce the complexity of your interface by presenting a single way to authenticate.**
  
  face ID나 touch ID가 실패했을 때는 사용자의 이름을 묻거나 암호를 묻는 등의 대안을 제공해야한다.
- **initiate authentication only in response to user action**

    버튼을 탭하는 것과 같이 명시적인 일로 사람들이 인증할 수있도록 하자.
- **always identify the authentication method you offer.**

    예를들어 Face ID로 앱을 로그인하는 경우, “로그인"과 문구 대신 “Face ID로 로그인" 처럼 명시적으로 표시
- **refer only to authentication methods that are available in the current context.**

    Face ID를 지원하는 기기에서 touch ID를 이야기하지말고, touchID만 지원하는 기기에서 Face ID얘기를 하지말아야한다. 관련 정보는 [LABiometry Type](https://developer.apple.com/documentation/localauthentication/labiometrytype)에서 얻을 수 있다.
- **In general, avoid offering a setting for opting in to biometric authentication within your app**

    앱 자체적으로 생체인증을 만들어 실행시키는 것은 하지말아라.