# HTML

> Hyper Text Markup Language

- 웹 표준을 만드는 곳은 W3C나 WHATWG에서 만들었는데 2019년에 단일 버전의 웹 표준이 만들어짐
- 표(table) 을 만들 때에는 `<th>`, `<table>`  태그 사용
- 목(Heading) 태그는 제목 이외에는 사용하지 않는 것이 좋음
- 리스트를 나열하기 위해서는 <li>태그를 사용
  - 순서가 있는 리스트 : ol, ul
  - 순서가 없는 리스트 : ul
  - 사용자 정의 리스트 : dl
- `<input>`, `<br>`, `<area>`, `<base>` 태그처럼 종료태그가 없는 경우도 있음

<br>

# CSS

> Cascading Style Sheets

- HTML과 CSS는 각자 문법을 갖는 별개의 언어
- 웹 브라우저는 내장 기본 스타일이 있어 CSS가 없어도 작동
- 자식 요소 프로퍼티는 부모의 프로퍼티를 상속 받지만 box model과 position는 상속받지 않음
- 디바이스마다 화면의 크기가 다른 것을 고려하여 상대 단위인 %를 사용
  - %, em, rem(폰트)
- id 값은 유일해야 하므로 중복되어서는 안됨
  - 중복해서 사용했다고 실행 안되거나 웹페이지가 안보이거나 하진 않음

- CSS 우선 순위
  - !important  >  inline style  >  id 선택자  >  class 선택자  >   요소선택자  >  소스 순서

<br>

## img, a

#### `img`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
  <header>
    <img src="C:/종우/Windows10/Desktop/TIL/ssafy/image/my_photo.png" alt="image">
  </header>
</body>
</html>
```

절대경로, 상대경로

```html
'''
<body>
  <header>
    <img src="C:/종우/Windows10/Desktop/TIL/ssafy/image/my_photo.png" alt="image">
  </header>
</body>
'''

변경하면
'''
<body>
  <header>
    <img src="../image/my_photo.png" alt="image">
  </header>
</body>
'''
```

<br>

#### `a태그`

> 하이퍼링크를 지정하는 a 태그

```html
'''
<body>
  <header>
    <a href="https://www.naver.com"></a><img src="../image/image.png" alt="image">
  </header>
</body>
'''
```

<br>

## nth-child()와 nth-of-type()

```html
'''
	<h2>어떻게 선택 될까?</h2>
    <p>첫번째 단락</p>
    <p>두번째 단락</p>
    <p>세번째 단락</p>
    <p>네번째 단락</p>
'''
```

```html
p:nth-child(2)   : 첫번째 단락이 빨강색으로 바뀜
p:nth-of-type(2) : 두번째 단락이 빨강색으로 바뀜
```

nth-child(n) : 부모 요소의 n번째 자식 요소. 모든 자식 중 순서만 맞다면 해당 요소를 선택

nth-of-type(n) : 순서 + type이 같은 자식 요소 중 n번째 요소를 선택

즉, nth-child는 h2부터 순서를 세지만,

nth-of-type은 같은 `<p></p>` 타입인 첫번째 단락부터 순서를 세기 때문에 둘의 답이 다르게 나온다.