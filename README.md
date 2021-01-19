# SCSS Masterclass

(S)CSS Layout Masterclass: Flexbox & Grid ([nomadcoder](https://nomadcoders.co/css-layout-masterclass))

## Flexbox

- First Rule: Flex Container Wrapper

    ```css
    display: flex;
    ```

- Main Axis and Cross Axis

  ![flexbox-axis](./assets/flexbox_axis.png)

  ```css
  flex-direction: row;    /* column, ... */
  ```

  - flex-direction: decise Main Axis ("row" is default)

  ```css
  justify-content: space-around;    /* flex-start, center, stretch, ... */
  ```

  - justify-content: change Main Axis's Item-Position

  ```css
  align-items: center;    /* flex-start, flex-end, ... */
  ```

  - align-items: change Cross Axis's Item-Position
