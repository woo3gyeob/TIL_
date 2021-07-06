## Sort, append, copy

<br>

## sorted(), sort()

sorted()와 .sort()의 차이점

```python
ls = [2,1,4,6,3]
sorted_ls = sorted(ls)
print('sorted 적용 ls : ', ls)
print('sorted 적용 sorted_ls : ', sorted_ls)
ls.sort()
print('sort 적용 ls : ', ls)
```

실행 결과

```python
'''
sorted 적용 ls :  [2, 1, 4, 6, 3]
sorted 적용 sorted_ls :  [1, 2, 3, 4, 6]
sort 적용 ls :  [1, 2, 3, 4, 6]
'''
```

- sorted() : 원본 데이터에 접근하지 않고 정렬한 데이터를 새로 할당한 변수에 할당

- sort() : 원본 데이터에 접근해서 정렬 수행



## extend() .append()

```python
# 문자열 추가하는 방식이 다름

string = ['ab','cd','ef']
print(string)
string.append('gh')
print('append 후 string : ', string)
string.extend('ij')
print('extend 후 string : ', string)
```

실행 결과

```python
'''
['ab', 'cd', 'ef']
append 후 string :  ['ab', 'cd', 'ef', 'gh']
extend 후 string :  ['ab', 'cd', 'ef', 'gh', 'i', 'j']
'''
```

- append() : 문자열 전체를 한 요소로 리스트에 추가
- extend() : 문자열 각 요소를 리스트에 추가



## shallow copy, deep copy

```python
a = [1,2,3,4,5]
b = a

a[2] = 5
print(a)
print(b)

id(a)
id(b)
```

실행 결과

```python
'''
[1, 2, 5, 4, 5]
[1, 2, 5, 4, 5]
a의 메모리 주소 :  2713646965952
b의 메모리 주소 :  2713646965952
'''
```

shallow copy(얕은 복사)는 같은 메모리 주소를 갖게 되서 다른 하나의 데이터를 변경하면 다른 하나의 데이터도 같이 변경된다.

서로 영향이 없게 하려면 deep copy(깊은 복사)를 해야한다

예)

```python
# 1번 방법 : copy 모듈 사용

import copy
a = [1,2,3]
b = copy.deepcopy(a) 
print(id(a), id(b))

# 2번 방법 : slicing 활용
a = [1,2,3]
b = a[:]
print(id(a), id(b))
```

실행결과

```python
2713646972480 2713646986560
2713647036672 2713647015552
```

