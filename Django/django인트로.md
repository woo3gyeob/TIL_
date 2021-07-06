# Django

### `웹의 프로토콜`

client-side : html, css, js

server-side : jsp, sql, php

`django` : python web framework

- 카페 창업 vs 프랜차이즈

- 쟝고 사용 기업 : spotify, instagram, dropbox, deliveryhero

- 파이썬으로 작성된 오픈소스 웹 어플리케이션 프레임워크

  #### `일반적인 디자인패턴` (MVC패턴)

  - 모델(Model)
  - 뷰(View)
  - 컨트롤러(Controller)

  #### `쟝고의 디자인패턴` (MTV)

  - 모델(Model) : 데이터베이스 관리
  - 템플릿(Template) : 레이아웃(화면)
  - 뷰(View) : 중심 컨트롤러(심장)

<br>

# Code

#### Django 서버 실행

파이썬 3.8.6 설정하고 git bash 켜서
`pip install django`

현재 설치된 패키지 확인 (django 3.1.x 있으면 ok)
`pip list`

프로젝트 생성 명령어
`django-admin startproject firstpjt`

서버를 켜는 명령어
`python manage.py runserver`

<br>

#### 프로젝트 폴더 안에 있는 파일 설명

- `__init__.py` : firstpjt 내의 다른 파일들을 하나의 모듈로 접근할 수 있도록 해주는 파일
- `asgi.py` : 쟝고 3버전을 쓰는데 새로 생김. 비동기적인 뭐 구동?
- `settings.py` : 굉장히 많이 사용. 쟝고 웹사이트의 모든 설정을 포함. 파일들의 위치, 디비 세부사항, 보안 
- `urls.py` : 이것도 중요. 사이트의 내부 연결을 지정.
- `wsgi.py` : asgi.py랑 비슷. 배포할 때 도움을 줌

<br>

#### 어플리케이션 만들기

앱 만들기

`python manage.py startapp 앱이름`

<br>

#### 앱이름/migrations 폴더 내 파일 설명

- `__init__.py` : 위에랑 비슷
- `admin.py` : 관리자 페이지를 관리하는 파일.
- `apps.py` : 앱에 대한 정보. 절대 수정 X
- `models.py` : MTV 디자인패턴의 model. 많이 사용
- `tests.py` : 테스트 코드 작성. 수정 X
- `views.py` : MTC 디자인패턴의 View. 많이 사용

<br>

#### 프로젝트에 어플리케이션 등록

**settings.py**에 **INSTALLED_APPS** = [ .... ]에 앱이름 추가

- 순서가 좀 중요하다. 보통 순서는 `local apps` > `3rd-party` > `django apps`

- LANGUAGE_CODE = 'ko-kr' 로 바꿔야 한국어 버전 사용 가능

- TIME_ZONE = 'Asia/Seoul' 로 바꿔줘야 서버 시간 한국으로 설정

<br>

#### url 등록

urls.py 에서

```python
urlpatterns = [
	path('admin/', admin.site.urls),
	path('index/', 'index.html'), # 사용 클라이언트가 메인 페이지로 들어오고자하는 요청을 보내면 index를 통해 View함수를 호출
]
```

views.py 에서

```python
# Create your views here.
def index(request): # 첫번째 인자는 항상 request로 받아야 함 (규칙! 필수!)
	return render(request, '템플릿경로') # 템플릿을 보여줄거다. render 함수의 첫 인자 항상 request
```

#### template 작성

앱이름/templates 폴더 생성

html 파일 생성

<br>

#### Filters

> DTL Syntax - Filters
>
> ex) {{ variable|filter }}, {{ name|lower }} name 변수를 모두 소문자로 출력
>
> ex) {{ variable|truncatewords:30 }}







