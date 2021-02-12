# Keywords & Functions

## fr (Fraction)

"fr" 단위는 기본적으로 사용 가능한 많은 공간을 차지합니다.

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
  grid-template-columns: repeat(5, minmax(auto, 1fr));
}
```

## auto-fill & auto-fit

행/열(Track)의 개수를 그리드 컨테이너(Container) 및 행/열 크기에 맞게 자동으로(암시적) 조정합니다.

repeat() 함수와 같이 사용하며, 행/열과 아이템(Item) 개수가 명확할 필요가 없거나 명확하지 않은 경우 유용합니다.(반응형 그리드 디자인을 할 수 있습니다.)

컨테이너의 크기가 아이템들을 수용하기 충분하지 않을 경우 아이템을 자동으로 줄 바꿈 처리하며, 그에 맞게 암시적 행/열도 자동으로 수정합니다.

auto-fill과 auto-fit의 차이점은 그리드 컨테이너가 하나의 행/열(Track)에 모든 아이템을 수용하고 남는 공간이 있을 때 발생합니다.
auto-fill은 남는 공간(빈 트랙)을 그대로 유지하여 가상의 그리드 셀로 Grid 영역을 채웁니다.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
}
```

auto-fit은 Item의 크기를 늘여서 남는 공간을 없앱니다.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
}
```

## min-content & max-content

min-content는 그리드 아이템이 포함하는 내용(Contents)의 최소 크기를 의미합니다.
max-content는 그리드 아이템이 포함하는 내용(Contents)의 최대 크기를 의미합니다.

- 한글을 사용하는 경우 `word-break: keep-all;`를 설정하면 정상적으로 동작합니다.

그리드 함수들과 같이 더 유용하게 활용할 수 있습니다.
다음 예제는 총 4컬럼 그리드를 생성하며 각 열(Track)은 최대 1fr 크기를 가지지만, max-content를 통해 포함된 그리드 아이템의 내용보다 작아질 수 없습니다.

```css
.grid {
  grid-template-columns: repeat(4, minmax(max-content, 1fr));
}
```
