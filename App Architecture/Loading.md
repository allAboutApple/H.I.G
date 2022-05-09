# Loading

콘텐츠가 로드 될 때 빈 화면이나 static screen은 앱이 정지되 것 처럼 보이게해서 혼란과 좌절을 야기하고 잠재적으로 사람들이 앱을 떠나게 만든다.

<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/80131e10-39eb-48e5-bdeb-5468b42c2504/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T155434Z&X-Amz-Expires=86400&X-Amz-Signature=bd7731c7baac289aa2eaa0cfbb2a20509c52c561c0735cfa1625f226bb3e51b3&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject" width = 600>

- **make it clear when loading is occurring**
  
    최소한 무언가 알리고있음을 나타내는 activity spinner를 보여줘야한다. 더 나아가 사람들이 대기 시간을 알 수 있도록 명확한 진행 상황을 표시하면 좋다.
    async bytes를 사용하면 이런게 쉽게 가능할 것 같다..!

- **show content as soon as possible**
    
    사람들이 화면을 볼 때 콘텐츠가 로드되기를 기다리게하지말아라! 즉시 화면을 표시하고 placeholder text, graphics, animations 를 사용해서 아직 컨텐츠를 사용할 수 없는 위치를 알려라.
    콘텐츠가 로드되면 이런 placeholder를 콘텐츠로 교체하자. background에서 content를 미리 로드하도록 하자.

- **educate or entertain people to mask loading time**
  
    게임 플레이, 재미있는 비디오, 흥미로운 placeholder graphics를 사용해서 힌트를 주자.
    
    [customLoading.mp4](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/50ef4546-f586-4e03-a4e4-0da57258d795/customLoading.mp4?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220509%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220509T155525Z&X-Amz-Expires=86400&X-Amz-Signature=24eb8f01e2a3bd465096d0a7927c71b921ca0e1eb5f4ed92e5ecaea033ceb777&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22customLoading.mp4%22&x-id=GetObject)
    
- **customize loading screens**
  
    standard progress indicator를 사용해도좋지만, 때로는 맥락이 맞지 않은 느낌을 줄 수도 있다.
앱이나 게임의 스타일에 맞는 맞춤형 애니메이션과 요소를 통해 보다 몰입감 있게 디자인해보자!