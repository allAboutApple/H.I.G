# **Undo and Redo**




많은 앱에서 기기를 shake하여 undo / redo를 할 수 있는데 만약 그렇게 undo / redo를 하려고하는 경우 alert을 띄워서 해당 작업을 실행할지에대한 확인을 받아야한다.

<br/>
<br/>

이 때 지침은

- **Briefly and precisely describe the operation to be undone or redone**
    
    undo와 redo alert 의 title에는 “Undo” or “Redo” 라는 접두사가 꼭 포함되게하자.  (후행에 공백도 포함해야된다) 접두사 뒤에는 간략하게 하고자하는 일에 대해 단어로 표현하자. 예를들어,
    Undo Name / Redo Address change
    

- **If you use the shake gesture for undo and redo, don’t use it for other actions**

    shake를 통해서 undo / redo를 제공하면서 또 다른 기능추가는 혼란스럽게한다.

- **Provide undo and redo buttons sparingly**

    너무 많은 undo / redo 버튼을 제공하게되면 혼란스럽기때문에 system icon을 사용해서 예상되는 위치 (navigation bar 등) 에 버튼을 제공하자.

- **Perform undo and redo operations in the current context only**

    Undo와 Redo는 이 전의 context가 아니라 현재 context에 명확하고 즉각적으로 영향을 주게해야한다.

[`UndoManager`](https://developer.apple.com/documentation/foundation/undomanager)를 통해서 개발 가이드를 확인할 수 있다.