# Authentication

> Authentication
>
> - 인증
> - 자신이 누구라고 주장하는 사람의 신원을 확인하는 것
>
> Authorization
>
> - 권한, 허가
> - 가고 싶은 곳으로 가도록 혹은 원하는 정보를 얻도록 하는 것

<br>

## Django Authentication system

쟝고는 Authentication + Authorization 합쳐짐

> - User object
> - Web request

쟝고의 built-in form

> - 회원가입(UserCreationForm)
> - 로그인(AuthenticationForm)

<br>

#### 로그인/로그아웃

로그인 : 세션을 create하는 기능과 같음

로그아웃 : request 객체를 받으며 return이 없음(세션을 delete하는 기능과 같음)

<br>

#### HTTP 특징

- 비연결지향(connectionless) : 서버는 응답 후 접속을 끊음
- 무상태(stateless) : 접속이 끊어지면 클라이언트와 서버 간의 통신이 끝나며 상태를 저장하지 않음

<br>

#### 쿠키
- 서버가 사용자의 웹 브라우저에 전송하는 작은 데이터조각
- 브라우저는 전송 받은 쿠키를 로컬이 key-value의 데이터 형식으로 저장
- 동일한 서버에 재요청시 저장된 쿠키를 함께 전송 ( 요청 + 쿠키 )
- 쿠키 사용 목적
  - 세션관리 : 로그인, 아이디 자동완성 등등
  - 개인화
  - 트래킹 

<br>

#### Session(세션)
- 사이트와 특정 브라우저 사이의 상태(state)를 유지시키는 것
- 클라이언트가 서버 접속시, 서버가 특정 session id를 발급. 클라이언트(브라우저)는 쿠키 저장

<br>

#### cookie lifetime(라이프타임, 일생)
Session cookie

 - 현재 세션 종료되면 삭제
 - 브라우저는 현재 세션이 종료되는 시기를 정의
 - 일부 브라우저는 다시 시작할 때 세션 복원을 사용해 계속 지속될 수 있도록 함

permanent cookie

 - Expires 속성에 지정된 날짜 혹은 Max-Age 속성에 지정된 기간이 지나면 삭제

<br>

<br>

#### 로그인폼 불러오기(built-in)
```python
from django.contrib.auth.forms import AuthenticationForm
.
.
def login(request):
    if request.method == 'POST':
        pass
    else:
        form = AuthenticationForm
    context = {
        'form':form,
    }
    return render(request, 'accounts/login.html', context)
```

#### 로그아웃

```html
<body>
  <div class="container">
    <h3>hello, {{ request.user }}</h3>
    <a href="{% url 'accounts:login' %}">Login</a>
    <form action="{% url 'accounts:logout' %}" method='POST'>     # 이거 추가
    {% csrf_token %}											  #ㅣ
    <input type="submit" value="logout">						  #ㅣ
    </form>														  #ㅣ
    {% block content %}
    {% endblock %}
  </div>
  .
  .
```

#### is_authenticated

- attribute. User class의 속성. User에 항상 True, AnonymousUser에 False

- ```html
  .
  .
  {% if request.user.is_authenticated %}
  <form action="{% url 'accounts:logout' %}" method='POST'>
  .
  .
  ```

- views.py에서

  ```python
  def login(request):
      if request.user.is_authenticated:
          return redirect('articles:index')
  ```

  

