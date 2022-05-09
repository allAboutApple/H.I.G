# Launching

launch 경험은 앱에대해 느끼는 방식에 상당한 영향을 미친다. 앱을 언제 마지막으로 열었는지의 여부와 상관없이 launch할 때의 시간은 빠르고 원활해야한다.

[Launching 디자인가이드](#Launch-디자인-가이드)

[Launching 개발가이드](#Launch-개발-가이드)




<br/>
<br/>
<br/>


## Launch 디자인 가이드

**1. Provide a luanch screen**
    
시스템은 앱이 시작되는 순간 launch화면을 표시하고 빠르게 앱의 첫 화면으로 교체한다. launch screen의 기능은 initial content load를 하는 동시에 사람들에게 빠르고 반응적이라는 인상을 주는 것이다.
launch화면에서 매끄럽게 전환하기위해서, 첫 번째 화면과 유사하게 디자인해야하며, launch screen자체가 주의를 이끌도록하지않아야한다. 
 
<br/>

   
**2. Launch in the appropriate orientation**
    
만약 앱이 세로 및 가로 모드를 지원하는 경우, 각 current orientation에 맞게 launch화면이 띄워지도록해야한다. 만약 앱이 하나의 orientation만 지원한다면, 사람들에게 디바이스를 회전하도록 해양한다. 
가로모드 앱은 기기가 왼쪽 또는 오른쪽으로 회전되어있는지 여부에 상관없이 제대로 보일 수 있게해야한다.
 
<br/>

   
**3. Avoid asking for setup information up front**
   
사람들은 앱이 제대로 작동하기를 원한다. 대다수의 사용자를 위해 앱을 디자인해야하며, 다른 configuration을 필요로하는 소수는 그들의 필요에따라 설정할 수 있게해야한다. 가능한 setup information을 디바이스의 설정이나 iCloud에서 얻도록하는 것이 좋다. 만약 setup information을 물어야한다면 사람들에게 앱을 처음 열 때 정보를 제공하고, 이후에 사람들이 설정에서 수정할 수 있도록해야한다.

<br/>


**4. Avoid showing in-app licensing agreements and disclaimers**
   
사람들이 앱을 다운로드하기 전에 라이센스를 읽을 수 있도록 App Store에 표기해야한다. 만약 이런 조항들을 app에 포함해야하는 경우, 사용자의 경험을 방해하지않도록해야한다.

<br/>


**5. Restore the previous state when app restarts.**
   
사람들이 앱이 시작되고나서 이 전의 상태로 되도록아가게끔 만들지말아야한다. 그들이 중단한 부분에서부터 다시 계속할 수 있도록 앱의 상태를 유지하고 복원해야한다.

<br/>


**6. Don’t encourage rebooting**
 
restarting은 시간도 많이 걸리고, 앱을 신뢰할 수 없게 만들고 사용하기 어렵게 만든다.
만약 앱에서 memory 또는 다른 이슈때문에 다시 리부팅하지않고는 다른 방법이 없는 경우, 이런 이슈에대해 나타내줘야한다.

<br/>

**7. Avoid asking people to rate your app too quickly or too often**

처음 출시 직후 또는, 사람들이 앱을 사용하는 동안 너무 잦은 평가 요청은 성가신 일이며, 유용한 피드백의 양이 줄어들 수 있다. 좋은 피드백을 받고싶다면 평가를 요청하기 이전에 사람들에게 앱에 대한 의견을 형성할 시간을 제공해야한다. 사람들에게 앱 평가를 강요하지말 것!

<br/>
<br/>
<br/>
<br/>
<br/>


## Launch 개발 가이드

app’s data structure를 초기화하고, 앱이 실행되도록 준비해야하고, 시스템으로부터의 launch time request에 대해 응답해야한다.

사용자가 홈 화면에서 앱 아이콘을 탭하면 시스템이 앱을 시작한다. 앱이 특정 이벤트를 request하는 경우, 시스템은 그 이벤트들을 핸들링하기위해 앱을 background에서 launch 한다. 
scene-based app일 경우, scenes 중 하나가 화면에 나타나거나 일부 작업을 수행해야할 때 시스템에서 이와 유사하게 launch할 수도 있다.

모든 앱은 ```UIApplication``` 객체가 나타내는 associated된 프로세스가 존재한다. 앱은 또한 ```UIApplicationDelegate```를 따르는 app delegate 를 가지고있어서, process에서 일어나는 중요한 이벤트에대해 응답한다. scene-based app에서도 app delegate를 통해서 launch 그리고 종료 와같은 기본적인 이벤트트들을 관리한다. launch time에 ```UIKit```은 app delegate와 ```UIApplication```객체를 자동적으로 만든다. 그런다음 앱의 Main event loop를 시작한다.

<br/>
<br/>


**→ Provide a Launch Storyboard**

사용자가 디바이스에서 처음 우리 앱을 Launch할 때, 앱이 UI를 표시하기 이 전까지 시스템은 launch storyboard를 display한다. launch storyboard를 display하는 것은 앱이 런치되었고 무언가를 하고있다를 나타낸다. 만약 앱이 자체적으로 초기화되고 UI를 빠르게 준비하는 경우, 사용자는 launch storyboard를 아주 짧게 볼 수도 있겠지?!

Xcode 프로젝트는 default launch storyboard를 만들어주고, 필용하다면 여러개의 launch stroyboard를 우리가 만들 수도 있다. launch storyboard를 만드는 방법은 아래의 과정을 따른다.

<center>
<img src= "https://s3.us-west-2.amazonaws.com/secure.notion-static.com/8f345b27-bee5-41af-889c-089c72c09ca3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2022-05-07_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_11.43.30.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T153754Z&X-Amz-Expires=86400&X-Amz-Signature=91b3eddf844fe534ab6fe3f55e91b7d6ff132c8fe5e357e1e227e6890cff52ce&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA%25202022-05-07%2520%25E1%2584%258B%25E1%2585%25A9%25E1%2584%2592%25E1%2585%25AE%252011.43.30.png%22&x-id=GetObject" width = 800>
</center>


⚠️ launch screen에 static image를 사용하지말아라!

iOS 14 이후부터, launch screen의 최대 크기가 25MB로 제한된다.

<br/>
<br/>
<br/>


**→ Initialize Your App’s Data Structures**

app launch time에 code initialization은 아래 두 함수 중 하나에 적절하게 선택해서 넣으면 됨.

- `application(_:willFinishLaunchingWithOptions:)`
- `application(_:didFinishLaunchingWithOptions:)`

앱이 시작되면 system에서 자동으로 처리하는 복잡한 일련의 단계가 있다. 간단하게 아래의 과정을 거친다.
<center>
<img src= "https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f7081d9b-655d-4243-9d88-44bd6f760d34/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T153958Z&X-Amz-Expires=86400&X-Amz-Signature=af793f08e0a38cf41a32e2857f43585769db3531ebe3f67db36412a5f114791a&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 500>
</center>

1. 유저 또는 시스템이 앱을 launch하면 system은 앱을 예열prewarms한다.
    - Prepare Your App For Prewarming
        
        iOS 15이후에서, 시스템은 기기의 조건에따라 앱을 prewarm할 수 있다. norunning application proesses를 실행해서 app이 사용되기 이 전에 유저의 wait time을 줄일 수 있다.
        prewarming은 main이 UIApplicationMain(_: _: _:_:) 을 호출할 때 까지 app launch sequence를 실행한다. 이를 통해 시스템이 완전한 full launch 이 전에  low-level structures를 준비하고 캐싱하고 빌드할 기회를 제공한다.
        더 자세한 내용은 [about the app launch sequence](https://developer.apple.com/documentation/uikit/app_and_environment/responding_to_the_launch_of_your_app/about_the_app_launch_sequence) 를 참고
        
2. 시스템은 Xcode가 제공하는 `main()`함수를 실행한다.
3. `main()` 함수는 `[UIApplicationMain(_:_:_:_:)](https://developer.apple.com/documentation/uikit/1622933-uiapplicationmain)` 를 호출하는데, 이는 `UIApplication` 인스턴스를 만들게되면서 app delegate를 인스턴스화한다.
4. `UIKit`은 Info.plist 파일에 지정되어있는 또는 target의 Custom iOS Target Properties 탭에서 지정한 default storyboard를 로드한다.  만약 앱이 default storyboard를 사용하지않으면 이 스텝은 생략
5. `UIKit`은 `application(_:willFinishLaunchingWithOptions:)` 함수를 호출한다.
6. `UIKit`은 state 복원을 실행하여 app delegate와 app’s viewcontroller에서의 추가적인 method를 실행한다. (자세한 내용은 [Preserving Your App’s UI Across Launches](https://developer.apple.com/documentation/uikit/view_controllers/preserving_your_app_s_ui_across_launches) 참고)
7. `UIKit`은 `application(_:didFinishLaunchingWithOptions:)` 함수를 호출한다.
<br/>


이 launch sequence가 지나가면 system은 app delegate 혹은 scene delegate를 통해 앱의 사용자 인터페이스를 표시하고 앱 life cycle을 관리한다.

이 때 불리는 app delegate의 `application(_:willFinishLaunchingWithOptions:)` 와 `application(_:didFinishLaunchingWithOptions:)` 에서 우리는 아래의 일들을 할 수 있다.

- app의 data structures를 초기화한다
- app이 동작할 때 필요한 resources가 있는지 검증한다.
- app이 처음 launch될 때 딱 한 번 setup되어야할 것에대해 수행한다. 
이 때 중요한 것은 절대 Main thread가 block되게해서는 안된다. 따라서 dispatch queue를 이용해서 일을 async하게 처리하도록해야하며 background thread에서 실행되도록해야한다.
만약 setup에서 사용자로부터의 Input이 필요하다면 `application(_:didFinishLaunchingWithOptions:)`에서만 처리하도록한다.
    - 서버로부터 필요한 data를 다운받는다.
    - document template이나 수정 가능한 데이터 파일을 app bundle에서 writable한 directory로 복사한다.
    - user에대한 default preference를 구성한다.
    - user accounts를 설정하거나 다른 required한 data를 모은다.
- 앱에서 사용하는 중요한 서비스들에대해 연결한다.
예를들어, 앱이 원격 notification 서비스를 제공한다면 Apple Push Notification servicce에 연결한다
- 왜 앱이 launch되었는지는 launch option dictioinary를 확인하면된다.

<br/>

앱이 scene-based가 아니라면 `UIKit`은 default user interface를 launch time에 자동으로 로드한다. `application(_:didFinishLaunchingWithOptions:)` 메서드를 활용해어 화면에 표시되기 전에 interface를 추가적으로 변경한다. 

<br/>
<br/>
<br/>


**→ Move Long-Running Tasks off the Main Thread**

user가 app을 Launch할 때, launch가 빠르게되는 것이 좋은 인상을 남긴다. `UIKit`은 `application(_:didFinishLaunchingWithOptions:)` 함수가 return할 때 까지 app의 인터페이스를 표시하지않는다. 따라서, `application(_:didFinishLaunchingWithOptions:)` 메서드 혹은 `application(_:willFinishLaunchingWithOptions:)`에서 long-running일을 수행하는 것은 앱이 느려보이게한다. 시스템이 앱의 백그라운드 실행 시간을 제한하기때문에 launch가 background에서 실행될 때 빠르게 짆애하는 것도 매!우! 중요하다.

앱의 initialization에서 중요하지 않은 작업은 launch-time에서 제거해라! 예를들어

- 앱에 즉시 필요하지않은 기능의 초기화를 연기하자
- 중요하고 오래걸리는 일의 작업을 앱의 main thread에서 옮기자. 
예를들어, global dispath queue에서 비동기적로 실행시키자.

<br/>
<br/>
<br/>

**→ Determine Why Your App Launched**

`UIKit`이 앱을 launch할 때, `application(_:willFinishLaunchingWithOptions:)` 와 `application(_:didFinishLaunchingWithOptions:)` 의 함수에 launch option dictionary를 넘긴다. dictionary의 key는 즉시 실행해야할 중요한 task를 알린다. 
예를들어, 유저가 어디서 앱을 시작했는지 그리고 앱에서 얻고자하는 것에대한 작업을 반영할 수 있다. 항상 예상하는 launch option dictionary key에 대한 내용을 확인하고 해당 존재에 적절하게 대응해야한다.


scene-based app에서의 경우, `UIKit`이 [application(_:configurationForConnecting:options:)](https://developer.apple.com/documentation/uikit/uiapplicationdelegate/3197905-application)
함수에 전달하는 option을 통해 왜 scene이 만들어졌는지 확인한다.


<br/>
<br/>
 

```swift
class AppDelegate: UIResponder, UIApplicationDelegate, 
               CLLocationManagerDelegate {
    
   let locationManager = CLLocationManager()
   func application(_ application: UIApplication,
              didFinishLaunchingWithOptions launchOptions:
              [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
       
      // If launched because of new location data,
      //  start the visits service right away.
      if let keys = launchOptions?.keys {
         if keys.contains(.location) {
            locationManager.delegate = self
            locationManager.startMonitoringVisits()
         }
      }
       
      return true
   }
   // other methods…
}
```

위 코드는 background location update에 대해 핸들링하는 app delegate를 나타낸다. location key가 존재하는경우, app은 location update를 미루지않고 즉시 실행한다. location update가 시작하면 Core Location framework는 새로운 location event를 전달 할 수 있다.

앱이 해당 기능을 지원하지않는 경우, location update에 대한 key를 제공하지않는다. 예를들어,해당 앱이 remote notification기능을 지원하지않는 경우 시스템은 remoteNotificaion key를 포함하고있지않는다.

launch option key는 [UIApplication.LaunchOptionsKey](https://developer.apple.com/documentation/uikit/uiapplication/launchoptionskey) 이고 key 목록은 아래와 같다

- `annotation`

앱에 전달된 URL에 source app에 맞는 custom annotation이 포함되어있음을 나타내는
- `bluetoothCentrals`

블루투스 관련 이벤트를 처리하기 위해 앱이 다시 시작되었음을 나타내는 key
- `bluttothPeripherals`

앱이 블루투스 주변 장치 개체와 associated된 작업을 계속해야함을 나타내는 key
- `cloudKitShareMetadata`

앱이 cloudKit share에 대한 초대를 수신했음을 나타내는 key
- `location`

수신 위치 이벤트를 처리하기위 앱이 실행되었음을 나타내는 key
- `newsstandDownloads`

새로운 newsstand asset을 처리하기위해 앱이 실행되었음을 나타내는 key
- `remoteNotification`

앱이 처리할 remote notification을 사용할 수 있음을 나타내는 key
- `shortcutItem`

사용자가 홈 화면 auick action에서 선택된 것에 대한 응답으로 앱이 실행되었음을 나타내는 key
- `sourceApplication`

다른 앱이 우리 앱 실행을 요청했음을 나타내는 key
- `url`

지정된 url을 열 수 있도록 앱이 실행되었음을 나타내는 key
- `userActivityDictionary`

사용자가 계속하려고하는 일에대한 것과 관련된 dictionary를 나타내는 key
- `userActivityType`

사용자가 계속하려고하는 일에 대한 활동유형을 나타는 key