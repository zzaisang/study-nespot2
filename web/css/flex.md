# flex

### flex는 layout 설정에 매우 도움이 되는 도구입니다.

- ie10이상부터 지원됩니다.(하지만 ie10은 구현 방법이 좀 다르기 때문에 ie11부터라고 생각해도 됩니다.)
- 보통 부모에 display:flex를 선언합니다.
- flex-direction default값은 row입니다.
- flex-direction은 축이라고 생각합시다.(축이 row이면 element는 column, column이면 elements는 row)
- justify-content는 축을 기준으로 정렬합니다.
- align-items는 축의 수직방향을 기준으로 정렬합니다. 
- flex-grow는 content폭을 제외한 여백을 공유합니다.
- flex-basis: 0으로 하면 content가 포함한 비율을 공유합니다.
- flex : 0으로 해주면 flex-basis, flex-grow를 실행한 것과 동일합니다.

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