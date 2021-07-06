# DRF

- JSON 포맷의 데이터로 응답하기 위해서는 DRF,  serializer도 제공하고, dictionary를 json 포맷으로 일일히 만들어도 된다

- DRF, POSTMAN 등에서 제공하는 기본 Form을 통해서 여러 HTTP Method를 테스트 해볼 수 있다.

- api_view 데코데이터를 사용해야 HTTP Method에 대한 요청에 응답할 수 있다.

- Serializers는 Queryset 객체를 JSON 포맷으로 변환 할 수 있는 python 데이터 타입으로 만들어준다.


<br>

## REST API

REST API 디자인 설계 시,

- 정보의 자원을 표현해야 하는 `URI`
- 자원의 대한 행위를 표현하는 `HTTP Method`

를 고려해야 한다

<br>

#### Serializers 사용 예시 코드

```python
from rest_framework import status

@api_view(['GET'])
def create(request):
    serializer = ModelSerializer(data=request.data)
    if serializer.is_valid(raise_exception=True):
        serializer.save()
        return Response(serializer.data, status=status.HTTP_201_created)
```

