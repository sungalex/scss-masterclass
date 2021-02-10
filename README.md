# SCSS Masterclass

(S)CSS Layout Masterclass: Flexbox & Grid ([nomadcoder](https://nomadcoders.co/css-layout-masterclass))

## Flexbox

- [x] flex-direction
- [x] justify-content
- [x] align-items
- [x] align-self
- [x] order
- [x] flex-wrap
- [x] reverse
- [x] align-content
- [x] flex-grow
- [x] flex-shrink
- [x] flex-basis

- First Rule: Flex Container Wrapper

  ```css
  .parent {
    display: flex; /* flex container로 설정 */
  }
  ```

  - flex item들의 부모 태그를 만들어서 flex container로 지정해야 함(dislplay: flex)
  - 대부분의 flex 설정은 부모 테그에 지정하고 자식 태그에 적용됨

- Main Axis and Cross Axis

  ```css
  .parent {
    display: flex;
    flex-direction: row;
    /* Main Axis */
    justify-content: space-around;
    /* Cross Axis */
    align-items: center;
  }
  ```

  ![flexbox-axis](./assets/flexbox_axis.png)

  - flex-direction: Main Axis 지정(default is "row")

  - justify-content: Main Axis의 아이템 정열 방식을 설정( flex-start, center, space-around, ... )

  - align-items: Cross Axis의 아이템 정열 방식을 설정( flex-start, flex-end, ... )

- flex-wrap

  - flexbox는 기본적으로 모든 아이템을 1줄에 유지하려고 함 (default is "flex-wrap: nowrap")
  - flex-wrap을 wrap으로 설정하면, 아이템 width 크기를 유지하여 여러 줄로 나누어 짐

    ```css
    .parent {
      flex-wrap: wrap; /* keep the item's width-size */
    }
    ```

- reverse : 아이템의 순서를 역순으로 변경함(flexbox에는 많은 reverse 설정들이 있음)

  ```css
  .parent {
    flex-direction: row-reverse; /* row, column, column-reverse, ... */
    flex-wrap: wrap-reverse; /* default is "nowrap" */
  }
  ```

- align-content : flex-wrap을 wrap으로 설정하여 여러 줄로 나뉘는 경우, 라인 간격 설정을 지정함

  - 설정 방식은 justify-content와 유사함

- Child Properties

  ```css
  .child:nth-child(1) {
    align-self: center;
    order: 1;
  }
  .child:nth-child(2) {
    align-self: flex-end;
    order: 2;
  }
  ```

  - align-self : align-items 처럼 Cross Axis 설정을 변경함 (단, 해당 아이템 하나 만 변경함)

    - 부모 태크(Wrapper)에 height가 정의되어 있어야 함

  - order : 아이템의 순서를 변경 (모든 아이템의 order 기본값은 "0")

    - order 값이 1 이상인 아이템들은 기본값("0")을 가진 아이템들의 뒤쪽으로 이동함 (order 값의 크기 순으로 정열함)

  ```css
  .child:nth-child(3) {
    background-color: #000;
    flex-shrink: 2; /* 다른 아이템 보다 2/5배 더 줄어듬 */
    flex-grow: 1; /* default is 0 */
  }

  .child:nth-child(4) {
    flex-shrink: 3; /* 다른 아이템 보다 3/5배 더 줄어듬 */
  }
  ```

  - flex-shrink: 전체 크기가 작아서 아이템의 크기가 줄어들 때 해당 아이템이 줄어드는 비율

    - 다른 아이템과 상대적으로 작아지는 비율(default 값은 1)
    - flex-wrap이 nowrap일 때 동작 (flex-wrap이 wrap으로 설정되어 있으면 아이템 크기가 줄어들지 않고 여러 줄로 나누어짐)

  - flex-grow: 아이템 크기를 늘여서 전체 여백을 채울 때 해당 아이템이 여백을 차지하는 비율

    - default는 0(아이템 크기가 늘어나지 않고 아이템 사이에 공백이 생김)

  - flex-basis : Main Axis의 element 처음 크기를 지정

    - flex-direction이 row이면 width를 지정하는 것과 같고, flex-direction이 column이면 height를 지정하는 것과 같음
    - element의 처음 크기를 지정하는 것이며, flex-shrink나 flex-grow에 의해 실제 크기는 변겨됨

- flexbox 연습 게임 : [Flexbox Froggy Game](https://flexboxfroggy.com/#ko)
