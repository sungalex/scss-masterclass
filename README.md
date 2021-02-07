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
- [ ] flex-grow
- [ ] flex-shrink
- [ ] flex-basis

- First Rule: Flex Container Wrapper

  ```css
  .parent {
    display: flex;
  }
  ```

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

  - flex-direction: decise Main Axis (default is "row")

    ![flexbox-axis](./assets/flexbox_axis.png)

  - justify-content: change Main Axis's Item-Positions ( flex-start, center, stretch, ... )

  - align-items: change Cross Axis's Item-Positions ( flex-start, flex-end, ... )

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

  - align-self : change Cross Axis like align-items (need to specify a height for the Parent)

  - order : change the order of item (default order is "0")

- flex-wrap

  - flexbox is basically trying to keep everything in one line (default is "flex-wrap: nowrap")

    ```css
    .parent {
      flex-wrap: wrap; /* keep the item's width-size */
    }
    ```

- reverse : reverse order of items (flexbox have many reverse)

  ```css
  .parent {
    flex-direction: row-reverse; /* row, column, column-reverse, ... */
    flex-wrap: wrap-reverse; /* default is "nowrap" */
  }
  ```

- align-content : modify the line

- Flexbox Froggy Game : https://flexboxfroggy.com/#ko
