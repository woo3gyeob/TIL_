## CSS flex-direction

Flex box의 주축을 변경하는 flex-direction의 4가지 값과 각각의 특징

```python
row : 요소들을 가로로
row-reverse : 요소들을 가로로 배치하되 역순으로
column : 요소들을 세로로
column-reverse : 요소들을 세로 역순으로
```

<br>

## Bootstrap flex-direction

flex-direction의 4가지 요소와 대응하는 bootstrap 클래스

```python
row : flew-row
row-reverse : flex-row-reverse
column : flex-column
flex-column-recerse
```

<br>

## align-items

align-items 속성의 4가지 값과 각각의 특징

```python
메인 축을 기준으로 (main-axis)
교차축(보조축)(cross-axis)에 적용

stretch : default
center : 보조축에서 가운데
start : 보조축의 첫번째
end : 보조축의 끝에
```

<br>

flex-flow 속성은 `flex-direction, flex-wrap`두가지 속성의 축약형

<br>

## Bootstrap Grid System

```html
<div class="container">
    <div class="row">
        <div class="col-__a__-__b__">
        </div>
    </div>
</div>
```



#### `Breakpoint prefix`

Bootstrap Grid System에서 요소의 크기를 지정하기 위한 클래스

> `__a__ `:  `xs, sm, md, lg, xl, xxl` 
>
> - breakpoint로 화면에 접속하는 기기의 환경(width)에 따라 어떤 화면을 보여줄지 설정
>
> `__b__`:  `1 ~ 12 `
>
> - 12 grid로 나눠져 있는 화면에서 얼마의 grid 만큼 차지해서 보여줄지 설정하는 값