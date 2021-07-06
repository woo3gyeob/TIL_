# 모델

> 모델을 하나하나 클래스로 만들것이다. 왜? 객체 관계 프로그래밍이니까
>
> 보통 앱이름의 단수형, 첫번째는 대문자로 작성
>
> 위에 models 클래스를 상속받을 것임. 왜? 테이블 구조 설정 외의 모든 기능을 다 사용할 수 있음

<br>

## Migrations (중요!!!!)

- 'django가 model에 생긴 변화(필드를 추가했다던가 모델을 삭제했다던가 등)를 반영하는 방법'
- Migration 실행 및 DB 스키마을 다루기 위한 명령어 
  - makemigrations : model 변경에 기반한 새로운 마이그레이션(like 설계도)을 만들 때 사용
  - migrate : 마이그레이션, 설계도를 실제 DB에 반영하기 위해 모델에서의 변경 사항들과 DB의 스키마가 동기화를 이룸
  - sqlmigrate : 마이그레이션에 대한 SQL 구문을 보기 위함. 
  - showmigrates : 프로젝트 전체의 마이그레이션 상태 확인용. 마이그레이션 파일들이 migrate 됐는지 여부 확인 용. 과정 상태가 어떤지 확인할 때. 

- #### 수정사항이 생겼을 때 : makemigrate
  - 수정사항 없이 migrate를 하면 메시지로 migrate 할게 없다고 메시지가 뜬다

  - ex) 터미널에 python manage.py migrate 하면 아무것도 안된다.

<br>

#### 반드시 기억해야 할 3단계

1. models.py
   - model 변경사항 발생
2. python manage.py makemigrations
   - migrations 파일 생성
3. python manage.py migrate
   - DB 적용

<br>

## DB API

- DB를 조작하기 위한 도구
- 쟝고가 기본적으로 ORM을 제공함에 따른 것으로 DB를 편하게 조작할 수 있도록 도와줌

#### 사용법(쿼리 만드는 법)
- `[Class Name].[Manager].[QuerySet API]`
- ex) Ariticle.objects.all()

#### Manager
 - django 모델에 데이터베이스 query 작업이 제공되는 인터페이스
 - 기본적으로 모든 django 모델 클래스에 objects라는 Manager를 추가

#### QuerySet

 - 데이터베이스로부터 전달받은 객체 목록
 - queryset 안의 객체는 0개, 1개 혹은 여러 개일 수 있음
 - 데이터베이스로부터 조회, 필터, 정렬 등을 수행

#### 왜쓸까?
 - 파이썬 언어로 작업하면서 DB와 소통하기 위한 중간 인터페이스라고 생각하면 됨

<br>

#### CRUD
- 대부분의 소프트웨어가 가지는 기본적인 데이터 처리 기능인
- create(생성), read(읽기), update(갱신), delete(삭제)



# CSRF token이란?
- db를 변경한다는 것
- 위험할 수도 있는 동작
- 데이터를 삭제한다? 수정한다? 위험하다..
CSRF token : 내가 만든 웹페이지에서 보낸 요청만 수락되게끔 하는 것

어떤 프로그램이든지 /create/ 요청을 아무나 보낼 수 있음!
그렇다면?
악의적으로 누군가가 /create/ 요청을 계속해서 악의적으로 보낼 수 있음!
그럼 어떻게 해결?
요청에 내가 만든 비밀 토큰이 존재하지 않으면 그 요청을 거부!! CSRF 라는 비밀 토큰!

결론! POST 메소드는 CSRF로 보안을 유지한다!

> 메서드
>
> - GET : url/q=검색어
> - POST : http url, method, body 이렇게 보내는데 body는 DB에서 수정할 내용?이 포함됨

