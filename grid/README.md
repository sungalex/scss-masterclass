# Grid

CSS Grid(그리드)는 2차원(행과 열)의 레이아웃 시스템을 제공합니다.
CSS Grid는 Container(컨테이너)와 Item(아이템)이라는 두 가지 개념으로 구분되어 있습니다.
Container는 Items를 감싸는 부모 요소이며, 그 안에서 각 Item을 배치할 수 있습니다.

- 참고 블로그 : [CSS Grid 완벽 가이드](https://heropy.blog/2019/08/17/css-grid/)

- [ ] grid-column-start
- [ ] grid-column-end
- [ ] grid-row-start
- [ ] grid-row-end
- [ ] grid-column
- [ ] grid-row
- [ ] grid-template
- [ ] justify-items
- [ ] align-items
- [ ] place-items
- [ ] justify-content
- [ ] align-content
- [ ] place-content
- [ ] justify-self
- [ ] align-self
- [ ] place-self
- [ ] grid-auto-rows
- [ ] grid-auto-flow
- [ ] grid-auto-columns

## CSS Grid Basic Concepts

Container에 "disply: grid"로 지정하면 Grid 레이아웃이 적용 됩니다.

```css
.parent {
  display: grid; /* 그리드 컨테이너(Container)를 정의 */
  grid-template-columns: 200px 200px 200px;
  grid-template-rows: 100px 50px 300px;
  column-gap: 5px;
  row-gap: 10px;
}
```

- [x] grid-template-columns : 컬럼의 갯수와 너비
- [x] grid-template-rows : 행의 갯수와 너비
- [x] column-gap : 컬럼 사이의 간격
- [x] row-gap : 행 사이의 간격
- [x] gap : 컬럼과 행의 간격 (행과 컬럼의 간격이 동일)

## Grid Template Areas

```css
.grid {
  display: grid;
  grid-template-columns: repeat(4, 200px);
  grid-template-rows: 100px repeat(2, 200px) 100px;
  grid-template-areas:  /* header, content, nav, footer는 Area 이름 */
    'header header header header'
    'content content content nav'
    'content content content nav'
    'footer footer footer footer';
}

.header {
  grid-area: header; /* Area 이름 지정 */
}
```

- [x] grid-template-areas : 영역(Area) 이름을 참조해 템플릿 생성
- [x] grid-area : grid-template-areas에서 사용할 Area의 이름을 지정
- [x] repeat()로 반복할 컬럼이나 행의 개수와 크기를 지정할 수 있다.
