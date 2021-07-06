# Form vs ModelForm
`Form`

 - model에 연관되지 않은 데이터를 받을 때 사용

`ModelForm`

 - 어떤 레코드를 만들어야 하는지 알고 있다.

<br>

#### for 태그 활용

```html
<form action="" method="POST">
  {% csrf_token %}
  {% for field in form %}
  {{ form.field.errors }}
  {% endfor %}
  <input type="submit">
</form>
```

#### bootstrap 입히기

> 어떻게? 태그의 속성값에 class를 주지?  ->  widjet!!!
>
> 단계
>
> 1) 구글에 django bootstrap 5 검색 후 첫번째꺼 눌러라
>
> - pip install django-bootstrap-v5
>
> 2) settings.py 에 등록해줘야함
>
> ```python
> INSTALLED_APPS = [
> 	'articles',
> 	'bootstrap5'
> ]
> ```
>
> 3) load 태그를 사용
>
> ```html
> {% extends 'base.html' %}
> {% load bootstrap5 %}
> 
> {% block content %}
> .
> .
> {% endblock  %}
> ```



## decorator

#### View decorators
- 어떤 함수에 기능을 추가하고 싶을 때, 해당 함수를 수정하지 않고 기능을 연장해주는 함수

- 예시

  - views.py의 index는 GET 메소드를 줘야 한다

    - ```python
      @require_safe
      def index(request):
      ```

  - views.py의 create는 POST, GET에 한해서 받을 것이다

    - ```python
      @require_http_methods(["GET", "POST"])
      def create(request):
      ```

  

  