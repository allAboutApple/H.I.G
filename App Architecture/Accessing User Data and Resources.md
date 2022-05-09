# Accessing Use Data

사용자의 개인 정보가 중요하다. 사람들이 앱을 신뢰할 수 있도록 하려면, 필요한 개인 정보 보호 관련 데이터와 resource, 사용 방법을 투명하게 공개하는 것이 중요하다. 

<br/>


<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/d70b6d8d-f157-49d3-b1a9-7748d90a6a13/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T160816Z&X-Amz-Expires=86400&X-Amz-Signature=cab6e9465da0a9070efa63dd5cd6ac9e693f169aafbc888e516b350bd0cdbee8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 300>

new 또는 update app을 제출할 때 개인정보 관련 관행 및 수집한 개인 정보 관련 데이터에 대한 세부 정보를 제공하야 App Store가 제품 페이지에 정보를 표시할 수 있다. ( 이 정보는 App Store Connect에서 언제든 관리 할 수 있다) 

사람들은 앱을 다운로드 하기 이 전에 제품 페이지의 privacy 정보를 사용하여 앱 다운로드에대한 결정을 내리게된다. 자세한 내용은 [App privacy details on the App Store](https://developer.apple.com/app-store/app-privacy-details/)를 확인!

<br/>
<br/>
<br/>


### **Requesting Access Permission**

사용자 데이터 또는 보호된 resource를 사용하려면, 먼저 사람들에게 허가를 받아야한다.

시스템은 사람들이 개인정보 또는 보호된 resource에 대한 엑세스 요청을 볼 수 있도록하는 standard alert을 제공한다. 앱이 그런 항목이 필요한 이유에대한 설명을 제공하면 시스템이 standard alert에 이 설명을 표시하게된다. 

사람들은 설정 > 개인정보 보호 에서 설명을 보고 선택적으로 항목을 업데이트 할 수 있다.

- **Request permission only when your app clearly needs access to the data or resource**

    사람들이 개인 접오 요청이나 장치 기능에 대한 access에 대해 의심하는 것은 당연한 일이다. 특히 필요없는 경우인데 permission을 요청하는 경우는 더더욱 그렇다. 이상적으로 사람들이 실제로 그 access가 필요한 기능에 도달할 떄 까지 권한 요청을 하지말아야한다. 
    
    위치요청같은 경우도, 위치 버튼을 사용할 때 사람들에게 방법을 제공하면 된다.
- **Request permission at launch only when the data or resource in necessary for your app to function**

    사람들은 app이 필요한 정보가 분명히 존재할 때 앱의 launch time 이 길어져서 방해받는 것을 좋아하지 않을 것이다. 사람들이 앱을 실행하는 즉시 앱 추적을 수행하려면 추적 데이터 수집하기 전에 시스템 제공 alert를 표시해야한다!
- **Write copy that clearly describes how your app uses the data or resource you’re requesting**

    standard alert는 앱 이름 뒤와 사람들이 권한 부여 혹은 거절하는 버튼 앞에 우리가 제공하는 설명을 노출한다. 이 문구는 간단하고 구체적이어야하며 이해하기 쉬운 짧고 완전한 문장으로 하는 것이 좋다.

    문장 형식의 대문자를 사용하고, 수동태를 피하고, 끝에 마침표를 포함해라. 

    개발자는 [Requesting Access to Protected Resources](https://developer.apple.com/documentation/uikit/protecting_the_user_s_privacy/requesting_access_to_protected_resources) 와 [App Tracking Transparency](https://developer.apple.com/documentation/apptrackingtransparency) 를 참고

문구에 대한 예시

| ⭕️ | The app records during the night to detect snoring sounds. | An active sentence that clearly describes how and why the app collects the data. |
| --- | --- | --- |
| ❌ | Microphone access is needed for a better experience. | A passive sentence that provides a vague, undefined justification. |
| ❌ | Turn on microphone access. | An imperative sentence that doesn’t provide any justification. |

<br/>
<br/>
<br/>


### **Displaying a Custom Screen Before a Permission Alert**

추가 세부 정보를 제공해야하는 경우, 시스템 경고가 표시되기 전에 사용자 지정 화면을 표시 할 수 있다. 
다음 지침들은 카메라, 마이크, 위치, 연락처, 캘린더 및 추적을 포함하여 보호된 데이터 및 리소스에 대한 엑세스 권한을 요청하는 system alert 전에 custom screen에 적용된다.

<br/>

**Include only one button and make it clear that it opens the system alert**

|  |  |
| ---------- | --- |
| <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/302f787b-d1d0-4f21-869b-5247104bfe67/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161006Z&X-Amz-Expires=86400&X-Amz-Signature=85c075d46add1e8bbb82d7b1da83abe5e865bf4c44d4dc9e62aeba2da9eaa9b0&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject"> | custom screen에 alert을 열지않는 버튼이 있으면 사용자가 선택하지 못하도록하는 경험을 줄 수 있어서 manipulated하게 느낄 수 있다.  “Allow” 라는 언어를 사용하여 사용자 정의 화면 버튼의 제목을 지정하는 것도 좋다. 화면에 보이는 버튼이 알림 허용 버튼과 유사해보이면 사람듬ㄹ은 의미 없이 계속 알림 허용 버튼을 누를 확률이 크다. 따라서 “continue” 혹은 “next”용어를 통해 버튼을 만들고, 해당 작업이 system alert을 띄우는 버튼임을 명확히 하는 것이 좋다. |


<br/>

**Don’t add additional actions to your custom screen**

| | |
| -- | -- |
| <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/6577d10a-deee-47e2-bdd2-6b181270e91c/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161203Z&X-Amz-Expires=86400&X-Amz-Signature=365f9677efa178545cb72edd8c58c189ed8c95bb4ba4ff024ea2f3c7a8300930&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 300> | 예를들어, screen을 떠날 수 있는 close 또는 cancel option을 제공하지 말아야한다.  |



<br/>
<br/>
<br/>


### **Clarifying Tracking Request**

앱의 추적은 민감한 문제이다. 어떤 경우에는 추적의 이점을 명확하게 설명하는 custom screen 을 표시하는 것이 도움이 될 수 있다.

Never precede the system-provided alert with a custom screen that coud confuse or mislead people.

사람들은 때때로 알림을 읽지 않고 무시하기위해 빠르게 탭한다. 이러한 행동을 이용하여 선택에 영향을 미치는 messaging은 App Store Review에서 거부될 것이다. 

거부되는 원인이 되는 몇 가지 금지된 custom screen design이 존재한다. 


 <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/9c71de0f-da83-4d40-8caa-6f0d7a3fc770/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161246Z&X-Amz-Expires=86400&X-Amz-Signature=c64c268050ad4728bb5a87e09c7ae8b7f501687a4be343a868851f46fd869ac2&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 150> <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/bff821c0-c57a-43a9-955b-13487b222df7/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161449Z&X-Amz-Expires=86400&X-Amz-Signature=752c3d4f496207aa2947867b69c5d18bad086ec11e1a6c88b493b6bd18a7f635&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 148 >  <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/28e30d03-a4ad-4493-a014-a08c7807edb6/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161459Z&X-Amz-Expires=86400&X-Amz-Signature=ed70d905e36ab66bd253eedf057ca5d63abf1a86e3253ae01ceec81f3518d6eb&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 141.5 >  <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/ce6e3078-de26-480f-89b1-9759047fc7a9/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161512Z&X-Amz-Expires=86400&X-Amz-Signature=bd1efdd459902c52657cb8940b495f2c3adf55eb5cd898809fb70e7ed15980b6&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 139 > 




<br/>
<br/>
<br/>



### **Using the Location Button**

iOS 15이후부터 Core Location에서 버튼을 제공한다.

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0b0d5a74-46ad-4d84-8fda-9f2212c9b310/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161644Z&X-Amz-Expires=86400&X-Amz-Signature=6ecf720592aeee1b8286443a40195d19fc99bd556de4a906d92a44043220df32&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 150>

따라서 사람들에게 필요한 순간에 자신의 위치에 엑세스 할수 있는 임시 권한을 앱에 부여할 수 있게된다. 앱에 승인 상태가 없는 경우, ,위치 버튼을 탭하면 standard alert에서 “한 번 허용”선택할 때 와 동일한 효과가 나타난다. 사람들이 이 전에 “앱 사용 중 허용”을 선택한 경우 해당 버튼을 누른다고 “한 번 허용"으로 바뀌지는 않는다. 더 자세한 개발적인 내용은 [CLLocatinoButton(Swift)](https://developer.apple.com/documentation/corelocationui/cllocationbutton)에서 볼 수 있다.

| | |
|--|--|
|<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0984d453-c0f4-430c-97b7-e95af9c8424f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T161727Z&X-Amz-Expires=86400&X-Amz-Signature=005d4d3480bb5d808f2ff06d9f6038c0c3580aa5f8950ddf187de8394f4ab459&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject"> | 사람들이 앱을 처음 열고, 위치 버튼을 탭하면 시스템에 standard alert이 표시된다. alert은 어떻게 버튼이 location에 access하는지에 대해 알 수 있게 하며, sharing이 시작될 때 location indicator를 나타내서 그들에게 remind시킨다. |

사람들이 앱을 처음 열고, 위치 버튼을 탭하면 시스템에 standard alert이 표시된다. alert은 어떻게 버튼이 location에 access하는지에 대해 알 수 있게 하며, sharing이 시작될 때 location indicator를 나타내서 그들에게 remind시킨다.

이후 사람들이 버튼의 동작에 대한 이해를 확인 한 후 앱에 자신의 위치에 대한 엑세스 권한을 한 번만 허용하고 싶을 때 위치 버튼을 탭하면된다. Consider using the location button to give people a lightweight way to share their location for specific app features.
위치버튼을 통해, 자신의 위치를 첨부한 게시글을 올릴 수 있음과, 상점을 찾거나, 등의 일을 할 수 있음을 상기시키자. 사람들이 앱에 한 번 허용 권한을 자주 부여한다는 사실을 알고 있다면, 위치버튼을 사용하여 버튼만 누르면 한 번 허용될 수 있게끔하는 이점을 생각해서 활용하자.

<br/>


Consider customizing the location button to harmonize with your UI

- “Current Location” 이라는 title을 custom할 수 있다.
- filled color나 outline location 에 대한 색상 선택이 된다
- select background color 그리고 title의 color를 선택할 수 있다.
- button corner radius를 조정할 수 있다.

사람들이 location button을 인식하고 신뢰할 수 있도록하는 다른 시각적 속성은 custom할 수 없다. 또한 반투명도와 같은 문제가 있어서, 버튼은 항상 읽기 쉬운 상태를 유지하도록 해야한다. 

<br/>
<br/>
<br/>



### **Using the Microphone in a ShazamKit App**

[ShazamKit](https://developer.apple.com/documentation/shazamkit)은 오디오 샘플을 ShazamKit catalog 또는 custom audio catalog와 일치시켜 오디오 인식을 가능하게한다. iOS 15이상의 앱에서 사용가능하다.

- 현재 재생중인 음악 장르에 맞는 그래픽으로 앱 경험 향상
- 오디오와 동기화되는 자막 또는 수화 제공
- 온라인 학습 및 retail 과 같은 맥락에서 가상 콘텐츠와 인앱 경험 동기화

앱이 인식할 오디오 샘픙르 가져오기 위해 device 마이크가 필요한 경우, 엑세스 권한을 요청해야한다. 모든 유형의 권한 요청과 마찬가지로, 사용자가 엑세스 권한을 요청하는 이유를 명확히 알 수 있도록 하는 것이 중요하다.마이크에대한 엑세스 권한을 받은 후에는 아래의 지침을 따르도록 해야한다.

<br/>

- **Stop recording as soon as possible**

    사람들이 앱의 인식을 위해 오디오 녹음을 허용할 때 마이크가 켜져있을 것이라는 것을 인식하지 못할 수 잇따. 따라서 필요한 샘플을 얻을 때 걸리는 시간 동안만 녹음하도록 해야한다.

- **Let people opt in to storing your app’s recognized songs to their iCloud library.**

    앱이 인식된 노래를 iCloud에 저장할 수 있는 경우 사람들에게 먼저 이 작업을 승인할 수 있는 방법을 제공해야된다.