# Django 정리

#### `MTV`

> Model : 데이터베이스 관련
>
> Template : 보여지는 것
>
> View : 그 외의 모든 컨트롤

<br>

#### `Templates/Static`

Django 프로젝트는 기본적으로 render 할 html과 같은 template 파일과 css, js와 같은 static 파일을 앱 폴더 내부의 templates와 static 이름의 폴더에서 찾는데,

> 만약 해당 위치가 아닌 임의의 위치에 파일을 위치 시키고 싶으면 
>
> `settings.py` 파일의
>
> `TEMPLATES  -  DIRS` 와
>
> `STATICFILES_DIRS` 라는 변수에 담긴 리스트의 요소를 정의

<br>

#### `Migrations`

> 1) 마이그레이션 생성 
>
> - python manage.py makemigrations
>
> 2) 마이그레이션 DB 반영 여부 확인 
>
> - python manage.py showmigrations
>
> 3) 마이그레이션에 대응되는 SQL문 출력 
>
> - python manage.py sqlmigrations .... 0001
>
> 4) 마이그레이션 파일의 내용을 DB에 최종 반영
>
> - python manage.py migrate

<br>

#### `Media`

사용자가 업로드한 파일이 저장되는 위치를 Django 프로젝트 폴더(crud) 내부의 /uploaded_files 폴더로 지정하려면 settings.py에

> - MEDIA_ROOT = BASE_DIR / 'uploaded_files'
> - MEDIA_URL = '/uploaded_files/'

<br>

#### `데이터베이스`

> RDBMS를 조작하기 위해서 SQL문을 사용
>
> SQL에서 명령어는 대소문자 다 가능
>
> 일반적인 SQL문에서는 세미콜론( ; )까지를 하나의 명령어로 간주
>
> SQLite에서 .tables, .headers on과 같은 dot( . )로 시작하는 명령어는 SQL문이 아님
>
> 하나의 데이터베이스 안에는 테이블이 여러개가 있어도 되고 없어도 된다

<br>











