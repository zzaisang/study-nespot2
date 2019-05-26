# flex

### 일명 flexbox라 불리는 Flexible Box module은 flexbox 인터페이스 내의 아이템 간 공간 배분과 강력한 정렬 기능을 제공하기 위한 1차원 레이아웃 모델 로 설계되었습니다

- ie10이상부터 지원됩니다.(하지만 ie10은 구현 방법이 조금 다르기 때문에 ie11부터 사용하는 것이 좋습니다.)
- 보통 부모에 display:flex를 선언합니다.
- flex-direction default값은 row입니다.
- flex-direction은 축이라고 생각합시다.(축이 row이면 element는 column, 축이 column이면 elements는 row)
- justify-content는 축을 기준으로 정렬합니다.
- align-items는 축의 수직방향을 기준으로 정렬합니다. 
- flex-grow는 content폭을 제외한 여백을 공유합니다.
- flex-basis: 0으로 하면 content가 포함한 비율을 공유합니다.
- flex는 flex-basis, flex-grow, flex-shrink를 축약한 표현입니다.

- 예제

```css
        .container {
            display: flex;
            flex-direction: row;
            justify-content: center;
            /*align-items: center;*/
            height: 80vh;
            background: gray;
        }

        .item {
            /*flex-grow: 1;*/
            /*flex-basis: 0;*/
            flex: 1;
            border: 3px solid black;
            background: white;
            font-size: 3rem;
        }

```

### 출저

- [인터랙티브 웹 개발 제대로 시작하기](https://www.inflearn.com/course/interactive_web#)