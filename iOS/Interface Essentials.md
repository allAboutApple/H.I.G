# Interface Essentials

대부분의 iOS app은 common interface element를 가진 framework인 UIKit에 있는 component를 이용하여 빌드된다. 이 프레임워크를 통해 앱은 시스템 전체에서 일관된 appearance를 가질 수 있고 높은 수준의 customization을 제공한다.
```UIKit```은 flexible하고 familiar하고 adaptable하므로 모든 iOS기기에 맞춰 single app을 디자인 할 수 있다.

```UIKit```에서 제공하는 인터페이스 요소는 세 가지 범주로 나눌 수 있다.

<br/>
<br/>

**1. Bars**

app에 어디에있는지를 알려주고, navigation을 제공하고, action을 시작하며 정보 전달을 위한 버튼 또는 기타 요소를 포함할 수 있다.

<br/>

**2. Views**

text, graphics, animations, interactive elements와같은 사람들이 앱에서 보는 주요 콘텐츠를 포함
view에는 scroll, insertion, deletion, arragement와 같은 것을 활성화할 수 있다.

<br/>

**3. Controls**

action을 시작하고 정보를 전달한다.
button, switches, textFields, progress indicator가 controls의 예시

iOS의 인터페이스를 정의하는 것 외에도 ```UIKit```은 앱이 채택할 수 있는 기능들을 정의한다.
예를들어 ```UIKit```을 통해 앱은 터치스크린의 제스처에 응답하고 drawing, accessibility, printing과 같은 기능을 활성화한다.

iOS에서 ```Apple Pay```, ```HealthKit```, ```ResearchKit```과 같은 다른 프레임워크 기술과도 통합하여 강력한 앱을 만들 수 있다.