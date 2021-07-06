# List

> upper() : 소문자를 대문자로
>
> lower() : 대문자를 소문자로

```python
def low_and_up(string):
    low_up_string = ''
    for order in range(len(string)):
        if order % 2: # 인덱스가 홀수인 경우
            low_up_string += string[order].upper()
        else: # 인덱스가 짝수인 경우
            low_up_string += string[order]
    return low_up_string

low_and_up('apple')
```

```python
# 조건표현식 활용
def low_and_up(string):
    low_up_string = ''
    for order in range(len(string)):
        low_up_string += string[order].upper() if order % 2 else string[order]
    return low_up_string

low_and_up('apple')
```

<br>

## remove() pop() del()

```python
def lonely(ls):
    new_ls = ls[:] # 같은거 나오면 원소 삭제할 리스트
    new_index = 1  # 삭제할 원소의 인덱스
    for index in range(1, len(ls)):
        if ls[index] == ls[index-1]:
            del new_ls[new_index] # 원소 삭제 메소드로 del()을 사용
        else:
            new_index +=1
    return new_ls

lonely([1,1,3,3,0,1,1])
```

:bulb: del()을 사용한 이유

리스트 원소 삭제 메소드는 pop, remove, del 정도가 있다.

- pop()은 가장 뒤 원소를 지우는 메소드
- remove() : 원래 이 메소드로 작성했다가 마지막에 1을 삭제할 때 자꾸 앞에 있는 1이 삭제되서 메소드 작동 원리를 다시 찾아봤다.
  - remove는 해당 원소의 값이 리스트에 있으면 삭제를 수행한다.
  - 다만, 리스트 맨 앞에서 수행
  - 따라서 반복문으로 인덱싱을 하다가 리스트 앞에 같은 값의 원소가 있으면 그 원소를 삭제
- del() : 위의 remove()의 문제 때문에 del() 메소드로 함수를 구현했다.
  - del()은 리스트와 인덱싱을 통해 값을 삭제
  - 앞의 리스트 원소부터 탐색하지 않으므로 해당 함수에 적합