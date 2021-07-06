# Event

#### `Event handler`

- EventTarget.addEventListener()
- 지정한 이벤트가 대상에 전달될 때마다 호출할 함수를 설정
- target.addEventListener(type, listener[, options])
  - type : 반응할 이벤트의 유형 (대소문자 구분 문자열)
  - listener : 지정된 타입의 이벤트가 발생했을 때 알림을 받는 객체
    - EventListener 인터페이스 혹은 JS function 객체(콜백함수) 여야 함

<br>

#### `addEventListener 하는 일`

- 특정 이벤트가 발생하면 할 일을 등록하자!
- EventTarget.addEventListener(type, listener)
- 예) 버튼.addEventListener(클릭, 새로고침) : 버튼을 클릭하면 새로고침을 하겠다!

<br>

#### `특징`

- document.createElement 메서드를 통해 HTML 요소를 생성할 수 있다

- EventTarget.addEventListener(type, listener)에서 listener에 작성되는 콜백 함수의 첫번째 매개변수는 발생한 이벤트를 설명하는 Event에 기반한 객체이다

- event.preventDefault 메서드를 통해 이벤트 동작을 취소할 수 있다

- 부모 노드에서 자식 노드를 추가하는 방법은 append, appendChild, insertBefore 메서드가 있다


<br>

#### `Event 종류`

> - click : 객체를 클릭했을 때
> - mouseover : 마우스 커서가 해당 객체 위에 있을 때
> - mouseout : 마우스 커서가 해당 객체에 있다가 밖으로 이동했을 때
> - keydown : 키보드 키가 눌렸을 때
> - keyup : 키보드 키에서 손 뗏을 때
> - load : 로딩이 끝났을 때
> - scroll : 스크롤 했을 때
> - change : input, select, textarea 태그 요소의 값이 변했을 때. input 이벤트와 달리 변화의 모든 과정에서 이벤트가 일어나진 않는다
> - input : input, select, textarea 태그 요소의 값이 변했을 때. 값이 변하는 모든 과정에서 이벤트 발생

<br>

##### `preventDefault()`

- 현재 이벤트의 기본 동작을 중단
- 태그의 기본 동작 (a태그는 클릭시 페이지 이동, form 태그는 폼 데이터를 전송)
- 이벤트의 전파를 막지 않고 이벤트의 기본 동작만 중단 (이벤트 자체는 발생하게 두는데 동작만 없앰!!)
  - 예) a태그 : 클릭했다는 이벤트는 남김, but 페이지로 넘어가는 동작은 발생 X