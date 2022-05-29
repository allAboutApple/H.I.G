# **Data Entry**

<br/>
<br/>

인터페이스 요소를 두드리든, 키보드를 사용하던지 정보를 입력하는 것은 지루한 과정일 수도 있다. 따라서 실제로 앱을 완벽히 시작하기 전에 너무 많은 사용자의 정보를 받아 프로세스 속도를 늦추는 것은 사람들이 빠르게 앱을 포기하는 길이 될 수 있음을 주의해야한다.

<br/>

- **when possible, present choices**

    데이터 입력을 가능한 한 효율적으로 만들어라. 예를들어 입력하는 것 보다 미리 정의된 것에서 선택하는 것이 더 쉬운 경우 `UITextField`가 아닌 `UITableView`나 `UIPicker` 사용을 고려하자
- **Get information from the system whenver possible**

    가능한 시스템에서 정보를 얻어야하는게 좋기때문에 사용자에게 permission을 통해서 캘린더나 연락처 같은 정보를 강제적으로 얻으려하지말자
- **Provide reasonable default values**

    필드의 기본 값을 가장 선택할 확률이 높은 가능성있는 값으로 채워놓자. 좋은 default value를 제공하면 의사결정을 최소화하고 프로세스 속도를 높일 수 있다
- **Enable advancement only after collection required values.**

    다음 또는 계속 버튼을 활성화하기 이전에 required field에 있는 값을 모두 채웠는지 확인하자. 버튼 활성화를 잘 활용해야한다.
- **Dynamically validate field values**

    긴 양식을 다 작성하고나서 다시 돌아가서 실수한 부분을 수정해야하는 경우 매우 답답할 수 있다. 따라서 입력 직후 필드 값을 확인하여 사용자가 즉시 수정할 수 있도록 하자.

- **Require field values only when necessary.**

    정말 필요한 정보에만 required field라고 명시하자
- Ease navigationthrough value lists

    ```UITableView```나 ```UIPicker```에서는 값을 선택하기 쉬워야한다. value list를 알파벳 순으로 정렬하거나 빠른 검색 및 선택을 용이하게하는 다른 논리적 방식으로 정렬을 고려해서 적용하자
- **Show a hint in a text field to help.**

    필드에 다른 텍스트가 없는 경우 placeholder로 “email”, “password” 처럼 표기할 수 있다. placholder로 충분히 설명이되는 경우 다른 설명문구는 굳이 추가하지말자.