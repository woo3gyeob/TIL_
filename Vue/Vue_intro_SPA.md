# Vue Intro

<br>

#### MPA(multi page app)

___

url - 서버 - html, js, css

- 화면 깜빡임
- 연결이 불안할 때

<br>

<br>

#### SPA(Single Page App)

___

- 애초에 한 번만 요청보내서 응답받고
- 나머지 화면 전환은 js로 해보자!
- 한 번의 요청에 필요한 모든 리소스(js, css, html,....)
- 특히 모바일 - 마치 네이티브앱인것처럼 만들 수 있었다 (js 덕분에)
- 웹 애플리케이션에 필요한 모든 정적 리소스를 한 번에 받고, 이후부터는 페이 지 갱신에 필요한 데이터만 전달받음
- Vue.js에서 말하는 ‘반응형’은 데이터가 변경되면 이에 반응하여, 연결된 DOM이 업 데이트되는 것을 의미

<br>

#### MVVM

___

- Model : JS object. Vue instance 내부에서 data로 사용됨. 값이 바뀌면 View(DOM)이 반응

- View : DOM(HTML). Data 변화에 따라 바뀜

- View Model : Vue instance. View와 Model 사이 Data와 DOM에 관련된 모든 일을 처리

<br>

<br>

# Vue

vscode에서 

> ####  `alt + b`

누르면 html 화면이 켜짐



#### `if / show 차이점`

- if : 아예 렌더링 안함 / 함
  - show 반대일 때
- show : 일단 렌더링은 하고, display 속성을 줌
  - 보였다 안보였다 하는 작업이 잦을 때



#### `computed / methods 차이점`

> #### `00_INTRO / 04_computed_method.html 에서 작업`

- computed
  - data에서 정의한 변수를 사용하지 않으면 data값이 변경되도 새로 불러오지 않아 반복을 줄일 수 있다!
- methods
  - app을 정의한 div는 값이 바뀌면 새로운 div를 불러오게 되는데
  - 그 때 methods도 항상 새로 불러오게 되서
  - 불필요한 반복이 발생



#### `computed / watch 차이점`

> #### `04_computed_watch.html 에서 작업`

> computed : data로 부터 계산된 어떤 값을 다른 곳에서 사용할 필요가 있을 때
>
> watch : data의 어떤 값이 변하면 어떤 동작이 필요할 때
>
> ex) 

- computed는 새 프로퍼티를 생성하지만 
- watch는 아무 프로퍼티도 생성하지 않고 익명함수는 단순히 콜백함수 역할만 함
- watch에 명시된 프로퍼티는 감시할 대상을 의미할 뿐임





#### `data`

- 데이터는 시간에 따라 변하는 것
  - 웹 구성에서 시간에 따라 변하는 것과 안변하는 것 구분해서 data에 넣을지 말지 고민이 필요



#### `this`

this를 제대로 사용하려면

- vue 옵션 object 모든 함수는 화살표 함수로 작성하지 않는다
- 하지만 콜백함수는 화살표 함수로 작성한다



