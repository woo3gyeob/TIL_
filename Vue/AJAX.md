# AJAX

- AJAX 정의
  - 비동기식 javascript와 XML 타입
  - 서버와 통신하기 위해 XMLHttpRequest 객체 활용
  - 요즘은 javascript의 장점때문에 Json 객체를 더 활용

- 동기식(Synchronous)
  - 순차적, 직렬적 태스크
  - 요청을 보낸 후 응답을 받아야만 다음 동작이 이루어짐(blocking)
- 비동기식(Asynchronous)
  - 병렬적 태스크 수행
  - 요청을 보낸  후 응답을 기다리지 않고 다음 동작이 이루어짐(non-blocking)
    - 즉, 요청 보내놓고 다음 태스크 수행

<br>

#### `왜 비동기를 사용하는가?`

- 사용자의 경험이 가장 중요
- 데이터 로드되는 중에 다 멈춰있으면 안됨. 병렬적인 비동기식이 적절
- blocking, Non Blocking을 동시에 요청해도 다른 응답이 온다

<br>

#### `Threads`

- 자바스크립트는 싱글 thread (단일 프로세스)
- 이를 보완하기 위해 동시성 모델(Concurrency model)
  - call stack : js 코드 실행하는 곳
  - web API : 
  - task Queue(Event Queue, Message Queue)
  - Event Loop
- 단점 : 들어간 순서대로 처리를 보장하지 못함
  - 왜? : call stack에 들어가는건 순차적일 지 몰라도 요청을 처리하고 task queue에 들어가는건 순서대로 안들어가기 때문
  - 이를 보완하기 위해 비동기식 call back 함수를 이용

<br>

## 비동기식 Asynchronous JS

- zero delays

- 순차적인 비동기 처리하기
  - Web API 들어오는 순서는 중요하지 않고, 어떤 이벤트가 먼저 처리되느냐가 중요(실행 순서 불명확)
  - 이를 해결하기 위해 순차적인 비동기 처리를 위한 2가지 작성 방식 존재
  - Async callbacks(비동기 콜백)
    - 백그라운드에서 실행을 시작할 함수를 호출할 때 인자로 지정된 함수
    - ex) addEventListener()의 두번째 인다
  - promise-style
    - Modern Web APIs에서의 새로운 코드 스타일
    - XMLHttpRequest 보다 조금 더 현대적인 버전
- 비동기 메서드 예시
  - **setTimeout**
    - Web API에서 동작이 완료 되면 call back Queue에 담겼다가 Call Stack이 비어있게 되면 event loop가 돌아서 할당하게 된다

<br>

<br>

## JS 함수는 "일급 객체(First-class object)"

- 일급 객체(일급 함수)
  - 다른 객체들에 적용 가능한 연산을 모두 지원하는 함수
- 조건
  - 인자로 넘길 수 있어야 함
  - 함수의 반환 값으로 사용할 수 있어야 함
  - 변수에 할당 할 수 있어야 함

<br>

## callback Hell

- 순차적인 연쇄 비동기 작업을 처리하기 위해

  - 콜백 함수를 호출

  - 다시 콜백 함수를 호출..

  - 또 다시 콜백 함수를 호출.....

    해버리면 계속 같은 패턴이 지속되고 반복됨

    이를 콜백 지옥이라 함(callback hell)

- 즉 여러개의 연쇄 비동기 작업을 하는 상황

- 문제

  - 디버깅 통제 어려움
  - 코드 가독성 떨어짐

<br>

## Promise

- 콜백 지옥 해결
- Promise 객체를 생성할 때 인자로 받는 callback 함수인 resolve와 reject는 비동기 처리가 성공/실패 했을 경우 어떠한 값을 전달할지 결정
- Promise 객체의 .then 메서드는 오류 없이 resolve 되었을 때 실행되는 함수
- .catch 메서드는 도중에 오류가 발생하여 reject 되었을 때 실행되는 함수

<br>

<br>

#### `동기와 비동기 차이`

> 코드에 대한 결과를 기다리느냐 안기다리느냐
>
> - 동기 함수 : 코드에 대한 결과가 나올 때까지 기다림
> - 비동기 함수 : 코드에 대한(요청에 대한) 결과를 기다리지 않고 다음으로 넘어감

<br>

#### `비동기 axios 요청 코드 예시`

```javascript
axios.get('https://api.example.com/data')
	.then(function (response) {
    	console.log(response.data)
	})
```

