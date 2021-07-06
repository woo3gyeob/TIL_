# Model Relationship

모델 간 관계를 나타내는 필드

> - Many to one(1:N)
>   - ForeignKey()
> - Many to Many(N:N)
>   - ManyToManyField()
> - One to One(1:1)
>   - OneToOneField()

<br>

ForeignKey's Arguments - On delete

> - CASCADE : 참조된 부모 객체가 삭제되면 참조하는 테이블의 객체도 삭제

<br>

## lookup

```python
Entry.objects.filter(pk__gt=4)
```

> - exact(일치)
> - contains(포함)
> - gt(큼)
> - gte(크거나같음)

<br>

# AUTH_USER_MODEL

> `커스텀 사용자`
>
> 원래 USER는 admin.py 등록 안해도 사용 가능했는데(built-in user) - 나중에 변경 불가
>
> 커스텀 사용자는 admin.py에 등록해야함
>
> 그냥 프로젝트 시작하기 전에 대체해라(쟝고 페이지에 찾아보면 됨(AUTH_USER_MODEL 찾아봐))
>
> docs.djangoproject.com/en/3.1/topics/auth/customizing/#substituting-a-custom-user-model

#### `AUTH_USER_MODEL이란?`

- User를 나타내는데 사용하는 모델
- 기본값은 'auth.User'
- 주의사항 : 프로젝트 중간에 변경 불가!!!! 마이그레이션 전에 바꿔야 함
- 커스터마이징 두개
	- AbstractBaseUser : 기본적으로 password, last_login만 제공
	- AbstractUser : 관리자 권한과 함께 완전한 사용자 모델 구현을 위한 기본 클래스

- abstract = True로 선언하면 테이블은 안만들어지고 서브클래스에게 기능만 제공해줌

  ```python
  class Meta:
  	abstract = True
  ```

- 프로젝트 중간(migrate 한번이라도 했으면)에 커스텀 유저 선언이 불가능!! 초기화 해야함!

  방법

  - 모든 설계도 파일을 지움
  2. 데이터베이스도 지움(db.sqlite3)
  3. 다 지웠으면 처음부터 migrate 하면 됨

<br>

#### 기본 유저(auth.User) 참조하는 유저모델

- AbstractBaseUser의 서브클래스
  - UserCreationForm
  - UserChangeForm

- 재정의 필요

  ```python
  from django.contrib.auth.forms import UserChangeForm, UserCreationForm
  from django.contrib.auth import get_user_model
  
  class CustomUserChangeForm(UserChangeForm):
  
      class Meta:
          model = get_user_model()
          fields = ('email', 'first_name', 'last_name',)
  
  
  class CustomUserCreationForm(UserCreationForm):
  
      class Meta(UserCreationForm.Meta):
          model = get_user_model()
          fields = UserCreationForm.Meta.fields + ('email',)
  ```

  - get_user_model 쓰는 이유 : 현재 활성화된 유저를 쓸 수 있음

<br>

<br>

## 역참조 Foreign key

> 1 : N 관계에서 N의 위치에서 역참조

특징

- Foreign key는 N의 위치에 작성해야 함			** 중요 **
- models.py에서 user를 참조하는 방법은 get_user_model 말고 'settings.AUTH_USER_MODEL' 써야함
- settings.AUTH_USER_MODEL
  - 유저 모델에 대한 외래 키 또는 M:N 관계를 정의할 때 사용
- 이건 settings.py에서 INSTALLED_APPS의 앱 실행순서때문에 get_user_model()을 쓸 수 없기 때문
- 즉, 앱 순서로 인한 꼬임을 아예 방지하기 위해 문자열로 참조
- django docs에서 'Referencing the User model' 참고!!

<br>

## 강의 요약!!

#### `models.py`에서는 User모델을 쓸 때 `settings.AUTH_USER_MODEL` 을 쓴다!!!!

#### `models.py`외의 다른 데서는 `get_user_model()` 을 쓴다!!!!



