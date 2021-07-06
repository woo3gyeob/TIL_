# REST API

#### `"프로그래밍을 통해 요청에 restful한 방식으로 json을 응답하는 서버 만들기!"`

<br>

### HTTP Method

___

- 자원에 대한 행위
- 즉 HTTP는 HTTP Method를 정의하여 주어진 자원에 수행하길 원하는 행동을 나타냄
- HTTP verb라고도 함

<br>

### HTTP Method 종류

___

- GET
  - 특정 자원의 표시를 요청, 오직 데이터 받기만 함
- POST
  - 서버로 데이터 전송, 서버에 변경사항 만듦 (CUD -> 이걸 이제 PUT, DELETE로 한다고?)
- PUT
  - 요청한 주소의 자원을 수정
- DELETE
  - 지정한 자원을 삭제

<br>

#### `HTTP/URL`

- URI는 정보의 자원을 표현하고, 자원에 대한 행위는 HTTP Method로 표현한다.

- HTTP Method는 GET, POST, PUT, DELETE가 있다. 

- 일반적으로 URI 마지막에 슬래시( / )는 포함하지 않는다.

- `https://www.fifa.com/worldcup/teams/team/43822/create/`는 계층 관계를 잘 표현 한 RESTful한 URI라고 할 수 있다?

  No. create 동사가 들어가 있고, teams와 team이 겹치므로 별로 좋지 않은 표현

<br>

#### `HTTP status code`

>- `200` : OK. 요청이 성공적으로 완료
>- `400` : Bad Request. 잘못된 문법으로 인하여 서버가 요청을 이해할 수 없음
>- `401` : Unauthorized. 유효하지 않은 자격 증명으로 요청이 적용되지 않음 (예: 로그인 안하고 좋아요를 눌렀을 때)
>- `403` : Forbidden. 서버에서 클라이언트가 누군지는 알고 있으나 승인되지 않음 (예: 내가 작성하지 않은 글을 삭제하려 할 때)
>- `404` : Not Found. 잘못된 URL
>- `500` : Internal Server Error. 서버 내부 오류

<br>

#### return HttpResponse(data, content_type='application/json') 에서

___

content_type이 뭘까?

- 이 문서가 어떤 타입인지 알려주는 인자
- 웹에서 F12/Network 탭 들어가보면 application/json 확인

<br>

#### serializers는 뭘까?

___

- 직렬화

- 데이터 구조나 객체 상태를 동일하거나 다른 컴퓨터 환경에 저장하고 나중에 재구성할 수 있는 포맷으로 변환하는 과정

- article을 json으로 변환해주는 변환기 역할
- 우리가 작성한 모델 구조 그대로 json, xml 등의 파일로 변환해 줌!
- django의 model 은 ModelForm, DRF는 ModelSerializer로 함!!!!!!!!!!!!

<br>

### `만약 DB 데이터 로딩하는 속도를 빠르게 해봐라! 라고 물어보면?`

> `데이터베이스 정규화`

관련된 내용이다!