# **Gesture**



사람들은 터치 스크린에 제스처를 수행해서 iOS 기기와 상호작용한다. 제스처를 통해 화면의 개체를 직접 조작하는 감각을 향상시킬 수 있다. 

일반적으로는 standard gesture를 사용한다. 게임이나 기타 몰입형 앱에서는 다른 custom gesture를 추가할 수 있지만 기본 앱에서는 사람들이 익숙하게 사용하는 standard gesture를 사용하자. 

<br/>
<br/>

- **Avoid interfering with systemwide screen-edge gesture**
    
    디바이스에따라 화면 가장자리를 제스쳐하게되면 app switcher, Notification Center, Control Center, Dock, Home screen 등으로 이동하게된다. 이 gesture는 모든 앱에서 적용되는 것인데 게임이나 몰입형 앱에서는 시스템 제스쳐보다 앱에서 사용하는 제스처에 우선순위를 두기도한다. 
    이렇게 앱 내의 제스처를 먼저 동작하게하고싶다면 UIViewController의 [preferredScreenEdgesDeferringSystemGestures](https://developer.apple.com/documentation/uikit/uiviewcontroller/2887512-preferredscreenedgesdeferringsys) 를 확인
    
- **Offer shortcut gestures to supplement, not replace, interface-based navigation and actions**
  
    가능하면 한 두번 더 탭해야하는 경우에도 탐색하거나 작업을 수행할 수 있도록 방법을 제공하자. 많은 앱에는 이전 홤녀으로 돌아갈 수 있는 명확한 버튼 또는 navigation bar 가 존재한다. 또는 사용자가 스와이프 제스처를 통해서 navigation을 pop하여 뒤로 돌아갈 수 있음에 염두하자.

- **Use multifinger gesture to enhance the experience of some apps.**

<br/>

Gesture에 대한 개발 지침은 [UIGestureRecognizer](https://developer.apple.com/documentation/uikit/uigesturerecognizer)를 확인하면된다. 

<br/>
<br/>
<br/>

### **Standard Gestures**

1. Tap
2. Drag
3. Flick (Scroll or pans quickly)
4. Swipe
5. Double tap
6. Pinch
7. Three-finger pinch (copy and paste)
8. Three-finger swipe (undo and redo)
9. Touch and hold
10. Rotate
11. Shake (undo or redo)