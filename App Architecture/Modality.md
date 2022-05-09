# Modality

modal은 명시적으로 종료를 할 수 있는 temporary mode에서 콘텐츠를 보여주는 디자인 기술이다. modal을 present하는 것은

1. 사람들이 독립적인 작업이나 밀접하게 관련된 options의 집합에 집중할 수 있게 된다.
2. 사람들이 중요한 정보를 받고 조치를 취하도록하는 것을 확실하게 표현한다.

![Untitled](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/aca4aba6-0bdd-4cf8-a5b5-833dec5bed1b/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T155705Z&X-Amz-Expires=86400&X-Amz-Signature=a6c062b5cd43ffa1bb0d9b045cb9d9eedb43436c8117d779ca6e37c9d443d117&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

다양한 system-defined model 경험을 위해 iOS에서는 alerts, activity views, share sheet, action sheet을 제공한다. custom model content를 표현하고싶다면 다음 스타일 중 하나를 사용할 수 있다.
이 스타일은 UIModalPresentationStyle에 정의되어있음!

- **automatic**

    default present style로 일반적으로 sheet이다.
- **fullscreen**
  이 전 뷰를 덮고 닫기 버튼이 필요한 스타일
- **overFullScreen**
- **popover**
  
  horitontally regular 디바이스 환경에서는 popover를 제공하고, compact한 환경에서는 sheet가 된다.
- **page sheet and form sheet**
    
    view의 일부를 cover하는 스타일.
- **custom**
  
  custom container에서 custom animation을 통해서 present할 수 있게
- **currentContext**
- **overCurrentContext**
- **blurOverFullScreen**

<br/>
<br/>
<br/>
<br/>

- **Use modality when it makes sense**
  
  현재 작업과 다른 작업을 선택하거나 수행하는데 사람들의 주의를 집중시키는 것이 중요한 경우에만 modal experience를 만들어라! modal experience는 사람들을 현재 context에서 벗어나게하고 dismiss action을 요구하기때문에 명확한 이점을 제공할 때만 사용하는 것이 좋다.
- **Reserve alerts for delivering essential - and ideally actionable - information**

    일반적으로 alert는 무언가 문제가 생겼을 때 나타난다. alert은 현재 경험을 중단하고 해재하려면 탭을 해야되기때문에 사람들이 interrupt당하는 것이 정당하다고 느낄 때 사용하는 것이 중요하다
- **In general, keep modal tasks simple, short, and narrowly focused**

    만약 modal tasks가 너무 복잡하면 모달 context에 들어갔을 때 일시 중단한 이 전의 작업을 놓칠 수도 있다. 따라서 앱 내에서 앱 처럼 느껴지는 big size의 모달을 만들지않는 것이 중요하다.

    특히 모달 작업 내에서 view hierarchy를 표시하는 것에 주의해야한다. 왜냐하면 사람들이 원래 작업으로 되돌아가는 방법을 잊어버릴 수 있기 때문이다. 모달 작업에 sub view가 포함되어야하는 경우, single path를 통해서 completion에 대한 명확한 경로를 제공해야한다.

    done button같은 경우, complete task가 아닌 경우 다른 용도로 사용하지않도록해야한다.
- **consider using a fullscreen modal style for immersive content or a complex task**

    full screen modal은 산만함을 최소화하므로, 비디오 사진, 카메라 view를 표시하거나 문서에 마크업 또는 사진 편집과 같은 multistep을 수행하는데 적합하다.
- **always include a button that dismisses the modal view**

    예를들어, done 또는 cancel버튼을 사용해야한다. button은 modal view에서 보조 기술에대해 제공할 수 있고 dismissal 제스쳐의 대안요소가 될 수 있다
- **when necessary, help people avoid data loss by getting confimation before closing a modal view**

    사람들이 view를 닫기 위해 제스쳐를 사용하던, 버튼을 사용하던 관계 없이 해당 작업으로 인해 사용자가 생성한 contents가 손실 될 수 있는 경우 상황을 설명하고 해결 법을 제공하는 action sheet을 제공해야한다. (예를들어 confirm button?)
- **make it easy to identify a modal view’s task**

    사람들이 modal view에 진입했을 때, 이전 context에서 벗어나 바로 돌아가지 않을 수 있따. model view의 task에 대한 title을 제공하거나 task를 설명하거나 guidance을 제공하는 추가 text를 제공하면 사람들이 앱에서 자신의 위치를 유지하도록 도울 수 있다.
- **coordinate the modal view’s appearance with your app**

    예를들어, modal view가 navigation bar를 가지고있으면 app에서 사용하는 navigation bar와 동일한 디자인을 사용해야한다.
- **choose a modal transition style that makes sense in your app**

    앱과 조화를 이후고 일시적인 context 이동에 대한 인식을 향상 시키는 transition style을 사용해야한다. 기본 transition은 modal view를 화면 하단에서 위로 수직으로 슬라이드하고 닫힐 때 다시 아래로 슬라이드한다. 
    
    앱 전체에서 일관적인 modal transition style을 사용해라.