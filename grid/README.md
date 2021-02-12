# Grid

CSS Grid(그리드)는 2차원(행과 열)의 레이아웃 시스템을 제공합니다.

![Gird](./img/grid.jpg)

CSS Grid는 Container(컨테이너)와 Item(아이템)이라는 두 가지 개념으로 구분되어 있습니다.

Container는 Items를 감싸는 부모 요소이며, 그 안에서 각 Item을 배치할 수 있습니다.

- nomadcoders 강의 외에 추가로 참고한 블로그 : [CSS Grid 완벽 가이드](https://heropy.blog/2019/08/17/css-grid/)

## CSS Grid Basic Concepts

"disply: grid"로 Grid Container(컨테이너)를 정의합니다.

정의된 컨테이너의 자식 요소들은 자동으로 Grid Items(아이템)로 정의됩니다.

```css
.grid {
  display: grid; /* 그리드 컨테이너(Container)를 정의 */
  grid-template-columns: 200px 200px 200px;
  grid-template-rows: 100px 50px 300px;
  column-gap: 5px;
  row-gap: 10px;
}
```

- [x] display
  - grid : Block 특성의 Grid Container를 정의
  - inline-grid : Inline 특성의 Grid Container를 정의
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
- [x] repeat()로 반복할 컬럼이나 행의 개수와 크기를 지정

## Columns and Rows

grid-template-areas를 사용하지 않고, grid-column-start/end, grid-row-start/end로 아이템의 시작 위치와 끝 위치를 지정해서 템플릿을 구성할 수 있습니다.

그리드 아이템의 시작 위치와 끝 위치는 Grid의 선 번호를 지정하며, 선 번호는 맨 왼쪽 시작 위치가 1입니다.

- 브라우저 개발자 도구 소스보기(검사)의 "Elements" 탭에서, HTML 소스의 Grid container 옆에 있는 <kbd>grid</kbd> 를 클릭하면 선 번호를 확인할 수 있음

```css
.header {
  grid-column-start: 1;
  grid-column-end: 5;
}
.content {
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

grid-column-start/end, grid-row-start/end를 단축해서 grid-column, grid-row로 지정할 수 있습니다.

- 속성을 "시작 위치 / 끝 위치" 형태로 지정

```css
.header {
  grid-column: 1 / 5;
}
.content {
  grid-column: 1 / 4;
  grid-row: 2 / 4;
}
```

- [x] grid-column : grid-column-xxx의 단축 속성(열 시작/끝 위치)
- [x] grid-row : grid-row-xxx의 단축 속성(행 시작/끝 위치)

grid-column의 끝 위치를 맨 끝("-1")에서 부터 역순번으로 지정 가능합니다.

```css
.header {
  grid-column: 1 / -1;
}
.content {
  grid-column: 1 / -2;
  grid-row: 2 / 4;
}
```

span으로 아이템이 크기를 지정할 수 있습니다. span을 사용하는 경우 시작 위치는 앞에서 부터 차례로 채워집니다.

- 아래의 예에서는 "content" 아이템의 column 크기 3개 뒤에 4번째 위치에 "nav" 아이템이 위치하게 됨

```css
.header {
  grid-column: span 4;
}
.content {
  grid-column: span 3;
  grid-row: span 2;
}
.nav {
  grid-row: span 2;
}
.footer {
  grid-column: span 4;
}
```

## Line Naming

"[ ]" 안에 선 번호에 대한 이름을 지정하여, 아이템의 시작과 끝 위치에 이 이름을 사용할 수 있습니다.

```css
.grid {
  display: grid;
  grid-template-columns: [line1] 200px [line2] 200px [line3] 200px [line4] 200px [line5];
}
.header {
  grid-column: line1 / line5;
}
```

## Grid Template

grid-template-columns, grid-template-rows 대신 아이템의 Area 이름으로 grid-template에 템플릿을 설정할 수 있습니다.

```css
.grid {
  display: grid;
  height: 50vh;
  grid-template:
    'header header' 1fr
    'content nav' 2fr
    'footer footer' 1fr / 3fr 1fr;
}
.header {
  grid-area: header;
}
```

- [x] grid-template : "`'area-name' 높이 / 넓이`" 형태로 지정
  - 넓이는 마지막 행에만 지정함

## Place Items

```css
.grid {
  display: grid;
  height: 50vh;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
  justify-items: end;
  align-items: streth;
}
```

- [x] justify-items : 가로 방향으로 아이템 정열 방식 지정
- [x] align-items : 세로 방향으로 아이템 정열 방식 지정

## Place Content

화면에서의 그리드의 배치를 조정하고자 할 때(그리드 전체를 움직이고자 할 때) justify-content, align-content를 사용합니다.

```css
.grid {
  display: grid;
  height: 100vh;
  grid-template-columns: repeat(4, 100px);
  grid-template-rows: repeat(4, 100px);
  justify-content: space-around;
  align-content: flex-start;
}
```

- [x] justify-content : 그리드 콘텐츠를 수평(행 축) 정렬
- [x] align-content : 그리드 콘텐츠를 수직(열 축) 정렬
- [x] place-content : justify-content, align-content을 각각 사용하는 대신 정열 방식을 한번에 지정
  - 예) `place-content: flex-start space-around;` (수직 정열 방식, 수평 정열 방식 순으로 지정)

## Single Gird Item Properties

단일 그리드 아이템을 수평, 수직 축으로 정렬하고자 할 때는 아이템 태그에 justify-self, align-self를 사용합니다.

```css
.header {
  justify-self: end;
  align-self: center;
}
```

- [x] justify-self : 하나의 그리드 아이템을 수평(행 축) 정렬
- [x] align-self : 하나의 그리드 아이템을 수직(열 축) 정렬
- [x] place-self : align-self와 justify-self의 단축 속성

## Auto Columns and Rows

지정한 아이템 수 보다 더 많은 Elements가 있는 경우, 행 축 방향으로 나머지 아이템들을 자동으로 표시 해줍니다.

Elements를 추가로 표시하는 방향을 grid-auto-flow로 설정할 수 있습니다. Default는 "row" 방향 입니다.

grid-auto-rows, grid-auto-columns으로 행이나 열에 자동으로 추가되는 아이템들의 암시적인 크기를 설정할 수 있습니다.

```css
.grid {
  display: grid;
  color: white;
  grid-template-columns: 100px;
  grid-template-rows: repeat(4, 100px);
  grid-auto-flow: column;
  grid-auto-columns: 100px;
}
```

- [x] grid-auto-flow : 추가 Elements의 자동 배치 방향을 정의
- [x] grid-auto-rows : 암시적인 행(Track)의 크기를 정의
- [x] grid-auto-columns : 암시적인 열(Track)의 크기를 정의
