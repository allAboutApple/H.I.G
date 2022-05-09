# Settings

일부 앱은 설정 또는 confifure 선택을 위한 방법을 제공할 수 있지만, 대부분의 앱에서는 그렇게 하는 것을 피할 수 있다. 좋은 앱의 대부분은 사람들에게 잘 작동하는 동시에 경험을 조정할 수 있는 몇 가지 방법을 제공한다.
대부분의 사람들이 기대하는 방식으로 앱이 작동하도록 디자인하면 설정의 필요성이 줄어들게된다.

<br/>
<br/>


- **infer what you can from the system**

    만약 user, device 또는 environment에 대한 정보가 필요한 경우, 유저에게 묻지 말고 가능하면 시스템에서 가져와야된다. 예를들어, location 에서 우편번호가 필요하게되면 사용자에게 입력을 요청하지말고 system으로부터 가져오는 방식이 가능하게 권한을 요청하자.
    
    만약 권한요청이 거부되었을 때는 수동입력을 가능하게하자!

- **thoughtfully prioritize configuration options within your app**

    
    앱의 메인 화면은 필수적이거나 자주 변경되는 option을 위한 좋은 장소이다. secondary screen은 가끔씩 변경되는 옵션에 대응하게하는 것이 좋다.

- **Expose infrequently changed configuration options in Settings**


    설정앱으로 가려면 현재 보고 잇는 앱에서 나가야하므로, 되도록이면 현재 앱 내에서 직접 설정을 조정하는 편으로 하는 것이 낫다. [Implementing an iOS Settings Bundle](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/UserDefaults/Preferences/Preferences.html) 와 [Preferences and Settings Programming Guide](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/UserDefaults/Introduction/Introduction.html) 를 참고해보면 좋다.

- **Provide shortcuts to Settings when appropriate**


    앱에 설정 > MyApp > 개인정보 > 위치 로 바로 갈 수 있는 어떤 항목을 제공할 경우 바로 설정앱을 열 수 있도록 해라. 가이드라인은 [openSettingsURLString](https://developer.apple.com/documentation/uikit/uiapplication/1623042-opensettingsurlstring) 와 [UIApplication](https://developer.apple.com/documentation/uikit/uiapplication) 참고!