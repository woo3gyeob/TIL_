# Model Relationship 2

<br>

## M:N (like, follow)

> - like  :  게시글과 사용자 (Article - User)
>
> - follow : 사용자와 사용자 (User - User)

<br>

#### `ManytoMany Field`

- Many To Many는 어느 모델에나 상관없이 작성 가능

- 여기서는 Article에다가 작성할 예정 (User를 따로 models에 정의하지 않았기 때문)

- ManytoMany Field 변수명은 복수형으로 작성!

<br>

### `like 기능 구현과정 요약`

> - related_name : 이미 같은 테이블을 참조하고 있으면 역참조 호출명을 따로 지정해줘야 한다
> - models.ManyToManyField
> - through : 중개테이블에 추가적인 필드를 활용해야 한다면 지정해줘야 함. 대신 쓰려는 필드도 다 만들어줘야 함
> - .add, .remove 사용
> - exists() : django 내에서 in 보다 속도가 빠름
>   - django는 캐시에 쿼리셋을 저장해 다음 평가때 사용하는데 이 때 쿼리셋의 크기가 크다면 속도도 느리고 캐시메모리 사용량이 커짐
>   - 하지만 exists()는 캐시에 저장하지 않고 바로 DB로 보냄
>   - 그래서 전체를 조회해야 하는 경우가 아니면 exists()가 훨신 최적화되어있음 

<br>

<br>

## FOLLOW (USER - USER)

> - follow는 보통 유저의 개인페이지에 존재
> - 그래서 먼저 프로필 페이지부터 만들거임!

<br>

### `기억!`

> - 참조 : followings
> - 역참조 : followers

