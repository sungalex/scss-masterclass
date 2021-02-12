# Keywords & Functions

- [ ] auto-fit
- [ ] auto-fill
- [ ] min-content
- [ ] max-content

## fr (Fraction)

"fr" 측정단위는 기본적으로 사용 가능한 많은 공간을 차지합니다.

fr의 크기는 navigator가 아닌 grid container 크기를 기준으로 계산합니다. 화면의 크기가 변하면 자동으로 화면의 크기에 맞춰 fr의 크기가 변합니다.

grid는 높이가 없기 때문에 row에 fr을 사용하려면 height를 지정해줘야 합니다.

```css
.grid {
  display: grid;
  height: 50vh; /* 화면 높이의 1/2 크기 */
  grid-template-columns: repeat(4, 1fr); /* 동일한 크기의 4개 아이템 */
  grid-template-rows: 1fr repeat(2, 2fr) 1fr;
}
```

## repeat()

`repeat(반복할 개수, 크기)` 함수로 속성에 반복할 컬럼이나 행의 개수와 크기를 지정할 수 있습니다.

## minmax()

minmax() 함수는 행/열(Track)의 ‘최소/최대 크기’를 정의합니다.
첫 번째 인수는 ‘최솟값’이고 두 번째 인수는 ‘최댓값’ 입니다.

grid-template-rows, grid-template-columns, grid-auto-rows 그리고 grid-auto-columns에서 사용합니다.

`minmax(최소 크기, 최대 크기)` 를 사용해 암시적 행/열(Track) 크기를 좀 더 유연하게 지정할 수 있습니다.
암시적 ‘행/열’의 크기를 auto로 지정하면 그리드 아이템의 크기에 따라 확장될 수 있습니다.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(5, minmax(100px, 1fr));
}
```
