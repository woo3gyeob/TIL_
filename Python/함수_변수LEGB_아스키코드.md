# 변수

#### `LEGB 법칙`

* `L`ocal scope: 정의된 함수


* `E`nclosed scope: 상위 함수 


* `G`lobal scope: 함수 밖의 변수 혹은 import된 모듈


* `B`uilt-in scope: 파이썬안에 내장되어 있는 함수 또는 속성

<br>

## 함수

- 함수는 오직 하나의 객체만 반환!
- return a, b 에서 a, b를 튜플로 반환하므로 같이 쓸 수 있음
- 함수에서 return을 작성하지 않으면 None 값을 반환
- 함수의 매개변수(parameter)는 함수를 선언할 때 설정한 값이며, 전달 인자(argument)는 함수를 호출할 때 넘겨주는 값
- 가변 인자를 설정할 때는 인자 앞에 * 을 붙이고, 이 때는 함수 내에서 tuple로 처리

<br>

## 재귀 함수

#### `장점`

- 코드 가독성을 높일 수 있음
- 코드 작성이 간편

#### `단점`

- 반복문보다 메모리 사용량 큼
  - 함수가 종료되기 전에 다시 함수를 호출하니까 마지막까지 가서 return 반환될 때까지 메모리 반환을 하지 않아 메모리 사용량이 큼
- 런타임이 김
- 최대 깊이 존재(메모리 한계로)
  - default로 설정되어 있지만 사용자가 지정할 수 있다.

<br>

## 아스키코드

> ord : 문자를 아스키 숫자로
>
> chr : 아스키 숫자를 문자로

#### `chr`

```python
def secret_word(ls):
    ascii_to_str = ''
    for i in ls:
        ascii_to_str += chr(i)
    return ascii_to_str
secret_word([80, 110, 66, 102, 90])
```

#### `ord`

```python
def secret_number(name):
    ascii_num_sum = 0
    for i in name:
        ascii_num_sum += ord(i)
    return ascii_num_sum
secret_number('jongwoo')
```



