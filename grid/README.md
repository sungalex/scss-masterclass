# Grid

CSS Grid(그리드)는 2차원(행과 열)의 레이아웃 시스템을 제공합니다.
CSS Grid는 Container(컨테이너)와 Item(아이템)이라는 두 가지 개념으로 구분되어 있습니다.
Container는 Items를 감싸는 부모 요소이며, 그 안에서 각 Item을 배치할 수 있습니다.

- 참고 블로그 : [CSS Grid 완벽 가이드](https://heropy.blog/2019/08/17/css-grid/)

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

## Columns and Rows

- grid-template-areas를 사용하지 않고 아이템의 시작 위치와 끝 위치를 지정해서 템플릿을 구성할 수 있다.

```css
.header {
  background-color: #2ecc71;
  grid-column-start: 1;
  grid-column-end: 5;
}

.content {
  background-color: #3498db;
  grid-column-start: 1;
  grid-column-end: 4;
  grid-row-start: 2;
  grid-row-end: 4;
}
```

- [x] grid-column-start : 그리드 아이템의 열 시작 위치 지정
- [x] grid-column-end : 그리드 아이템의 열 끝 위치 지정
- [x] grid-row-start : 그리드 아이템(Item)의 행 시작 위치 지정
- [x] grid-row-end : 그리드 아이템의 행 끝 위치 지정

- 그리드 아이템의 시작 위치와 끝 위치는 Grid의 선 번호를 지정하며, 선 번호는 맨 왼쪽 시작 위치가 1이다.
  브라우저 소스보기(검사) 개발자 도구의 "Elements" 탭에서, HTML 소스의 Grid container 옆에 있는 <kbd>grid</kbd> 를 클릭하면 선 번호를 확인할 수 있다.
