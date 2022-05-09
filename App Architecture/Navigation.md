# Navigation

사람들은 그들의 예상에 미치기 전까지 앱의 navigation을 인식하지 못하는 경향이 있다. 우리의 임무는 앱 자체에 주의를 기울이지 않고, 앱의 구조와 목적을 지원하는 방식으로 navigation을 구현해야한다. 

navigation은 자연스럽고 친숙하게 느껴져야하며 인터페이스를 지배하거나 contents에서 초점이 멀어지게하면 안된다.

<br/>
<br/>

iOS에서는 총 3가지 스타일의 navigation이 존재한다.

<br/>
<br/>

### **1. Hierarchical Navigation**

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/f64a1c2a-f23d-4dad-af7e-a5b8759cbf6b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T160229Z&X-Amz-Expires=86400&X-Amz-Signature=a4c9b80294e285072a1edaceac8c20c4b035905ebc253e40a148ea8304a321d8&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 500>

목적에 도달하기  까지 화면 당 하나의 선택을 한다. 다른 목적지로 가려면 단계를 다시 추적하거나 처음부터 다시 시작하여 다른 선택을 하도록한다. 

setting과 mail 앱은 이런 navigation style을 구성한다.

<br/>
<br/>

### **2. Flat Navigation**
<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/53a419a0-0f96-45df-88c5-76fca40a5e13/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T160241Z&X-Amz-Expires=86400&X-Amz-Signature=5f34143b77a15e64ed6bccb065a280147eb54ffa2104467c5f489a0a80d39cf7&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 500>


여러 컨텐츠 범주 간에 전환이 있다. 
Music과 App Store가 이런 navigation style을 구성한다.

<br/>
<br/>

### **3. Content-Driven or Experience-Driven Navigation**

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/71eb7448-66e4-4290-88e3-41bef98e5a8b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T160251Z&X-Amz-Expires=86400&X-Amz-Signature=eba576d9b2bf4d199fca12801739ab07fffce5aa06426e26a4c44fc0dd4e29af&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 500>


콘텐츠를 통해 자유롭게 이동하거나 콘텐츠 자체가 navigation이 되는 구성이다.

Games, books, 다른 몰입형 앱은 일반적으로 이런 navigatino style을 구성한다.

일부 앱은 여러 navigation style을 결합하기도한다. 예를들어 flat navigation은 각 범주 내에서 hierarchical navigation을 가지기도한다.

<br/>
<br/>


- **Always provide a clear path**

    사람들은 앱에서 자신의 위치와 다음 목적지로 가는 방법에 대해 알고 있어야한다. navigation style에 관계 없이 content 경로는 논리적이로 예측 가능하며 따르기 쉬워야한다. 일반적으로 사람들에게 각 화면에 대한 하나의 경로를 제공해야한다.여러 context에서 화면을 봐야하는 경우, action sheet, alert, popover, modal view를 사용하는 것이 좋다.
- **Design an information structure that makes it fase and easy to get to content**

    최소한의 탭, 스와이프 및 화면이 필요한 방식으로 information structure를 구성해야한다.
- **Use touch gestures to create fluidity**

    최소한의 friction으로 인터페이스를 쉽게 이동할 수 있다. 예를들어 사람들이 화면 측면에서 스와이프하여 이 전 화면으로 돌아가도록할 수 있다.
- **Use standard navigation components**

    가능하면 page control, tab bars, segment control, tableView, collectionView, splitview 와 같은 standard navigation control을 사용하자. 사용자는 이미 여러 control에 익숙하며 앱을 탐색하는 방법을 직관적으로 알 수 있다.
- **Use a navigation bar to traverse a hierarchy of data**

    navigation bar 타이틀은 current position을 나타낼 수 있으며, back button을 통해 이 전 위치로 쉽게 돌아갈 수 있다.
- **Use a tab bar to present peer categories of content of functionality**

    tabbar를 사용하면 현재 위치에 관계 없이 categories간의 빠른 전환을 할 수 있다.
- **On iPad, use a split view instead of a tab bar**

    split view는 tab bar와 동일한 빠른 탐색을 제공하는 동시에 대형 디스플레이를 잘 활용하는 방법이다.
- **Use a page control when you have multiple pages of the same type of content**

    page control은 사용 가능한 페이지 수와 현재 활성화 된 페이지를 명확히 나타낸다. 날씨 앱은 페이지 컨트롤을 사용하여 위치 별 날시 페이지를 표시한다.