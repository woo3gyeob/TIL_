# Model Relationship

> 1) ForeignKey는 부모 테이블의 데이터를 참조하기 위한 키이다. 
>
> 2) 1:N 관계에서 1은 N의 데이터를 역참조
>
> 3) on_delete 속성은 ForeignKey 필드의 필수 인자이다. 
>
> 4) 1:N 관계에서 외래 키는 유일한 값이면(Unique 하면) PK가 아니어도 상관없다.

<br>

<br>

## 1:N with User

> 유저모델 참조하는 두가지 방법
>
> - settings.AUTH_USER_MODEL  :  models일때 (문자열 반환)
> - get_user_model() : models.py 외의 모든 파일 ( 객체 반환)

예시

```python
class Article(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)   # 추가
    title = ...
```

<br>

<br>

### 작성날짜/수정날짜 형식을 휴먼틱한 형식으로

___

구글에 django humanize naturaltime 또는 naturalday 검색

```python
# settings.py의 INSTALLED_APPS에 맨 밑에 이거 추가
'django.contrib.humanize',

# html 파일에 추가
{% extends 'base.html' %}
{% load humanize %}			# 추가

{% block content %}
  <p>작성시각 : {{ article.created_at|naturalday }}</p>		# 수정
  <p>수정시각 : {{ article.updated_at|naturaltime }}</p>	# 수정
  <hr>
```

