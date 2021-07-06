# JS - AJAX

#### `JS 상식`

- Event Loop는 Call Stack이 비워지면 Task Queue의 함수들을 Call Stack으로 할당

- XMLHttpRequest(XHR)은 AJAX 요청을 생성하는 JavaScript API이다. XHR의 메서드 로 브라우저와 서버간의 네트워크 요청을 전송

- axios는 XHR(XMLHttpRequest)을 보내고 응답 결과를 Promise 객체로 반환해주는 라이브러리


<br>

#### `아래의 코드가 실행되었을 때 Web API, Task Queue, Call Stack 그리고 Event Loop에서 어떤 동작이 일어날까`

```javascript
console.log('1')
setTimeout(function () {
    console.log('2')
}, 2000)
console.log('3')
```

> console.log('1') -> OUTPUT
>
> setTimeout(function () {console.log("2")}, 2000) -> call stack -> OUTPUT
>
> console.log('3') -> call stack -> OUTPUT
>
> Web API(setTimeout 돌아감) -> task Queue -> callstack 비어있는 경우 -> call stack -> OUTPUT
>
> '1' -> '3' -> '2'

<br>

## Concurrency

>  JS는 Event loop를 기반으로 하는 Concurrency model을 가지고 있다

#### `Concurrency vs Parallelism`

> Concurrency(동시성)
>
> - 시간을 나누어 여러개의 thread를 번갈아가면서 진행하는 방식. 동시에 진행하는 것처럼 보임
>
> Parallelism(병렬성)
>
> - 여러개의 core를 사용하여 실제로 동시에 진행하는 것

<br>

<br>

## 상식

코어 수?

스레드 수?

클럭

캐시 메모리

- cpu안에 내장되어 있음
  - 캐시메모리가 크면 속도 향상
  - 하지만 자주 참조하지 않은 데이터를 굳이 빠른 속도로 보낼 필요 없다면 메모리 RAM, 또는 HDD에 저장 후 관리
- 속도가 굉장히 빠름
- 비쌈

메모리 RAM

- 캐시메모리에서 다룰 필요 없이 적당히 참조하는 데이터를 저장

- 속도가 적당히 빠름
- 적당히 비쌈

대용량저장장치 HDD SDD

- 정말 가끔 참조하는 데이터 저장

- 속도가 느림
- 가장 쌈









