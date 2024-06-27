## CSS
- Cascading Style Sheets의 약자로 HTML 문서에 색이나 모양, 출력 위치 등 외관을 꾸미는 언어
- 셀렉터, 프로퍼티, 값으로 구성
    - ,로 여러개/#id/.class/* 전체/input[type=text] 특정속성/a:hover 가상클래스/p::before 가상요소
- 부모 태그로부터 상속

## Box Model
모든 요소를 하나의 직사각형 박스로 여기는 모델
- Content: 글이나 이미지 등 요소의 실제 내용
- Padding: 안쪽 여백. background-color는 tag의 background-color
- Border: 패딩 외부 테두리
- Margin: 바깥 여백으로 인접 태그와 만나는 공간. background-color는 투명

### box-sizing
width height의 기준을 정할 수 있음
- content-box: padding 영역 부터 포함하지 않음
- border-box: margin 영역 부터 포함하지 않음

### background
background-position / background-size / object-fit / object-position 속성으로 조절

## display:none vs visibiliy:hidden
display:none 스타일을 가진 태그는 공간이 할당되지도 않고 보이지도 않음. visibility:hidden 스타일의 경우 공간은 할당되지만 보이지 않음.

## position
문서 상에 요소를 배치하는 방법 지정
- static: 요소를 일반적인 문서 흐름에 따라 배치. trbl의 값은 위치에 영향을 주지않음.
- relative: static + 자신을 기준으로 top right bottom left의 값에 따라 오프셋 적용
- absolute: 요소를 일반적인 문서 흐름에서 제거하고 가장 가까운 위치 지정 조상 요소에 대해 상대적으로 배치
- fixed: 요소를 일반적인 문서 흐름에서 제거하고 뷰포트의 특정 위치에 고정시키는 배치.
- sticky: 최초에는 relative와 같이 동작하다가 스크롤시 지정 지점에서 요소가 고정. 부모는 높이가 있어야 하고 overflow 변경하지 않아야함.

## display
|특징|block|inline|inline-block|
|------|---|---|---|
|새 라인|항상|라인 안|라인 안|
|배치|블록 박스 내|모든 박스 내|모든 박스 내|
|옆의 요소|배치 불가|배치 가능|배치 가능|
|넓이|기본 넓이가 부모 넓이|.|.|
|크기 조절|가능|불가|가능
|마진/패딩 조절|가능|상하 마진/패딩 불가|가능|

flex, grid, table

## flex
- 부모 요소(flex container) 자식요소(flex item) 컨테이너가 flex의 영향을 받는 전체 공간이고 설정된 속성에 딸라 각각의 아이템들이 어떤 형태로 배치 되는 것.
### 컨테이너에 적용
- display: flex
- flex-direction: 메인축의 방향 설정
- flex-wrap: 줄바꿈 처리
- jusfify-content: 메인축 방향 정렬
- align-items: 수직축 방향 정렬 stretch가 기본값, flex-end하면 아래로 붙기
- align-content: wrap한 상태에서 2줄 이상 되었을 때, 여러 행 정렬
### 아이템에 적용
- flex-basis: flex 아이템의 기본 크기
- flex-grow: 유연하게 늘리기, basis의 값보다 커질 수 있는지 결정. basis를 제외한 여백 부분을 지정된 숫자의 비율로 나누어 가짐.
- flex-shrink: 유연하게 줄이기, basis의 값보다 작아질 수 있는지 결정. 0으로 세팅하면 줄어들지 않음.
- align-self: 수직축 정렬
- order: 시각적 나열 순서, html자체의 구조를 바꾸는 것은 아님

## grid
- flex가 한 방향 레이아웃 시스템이었다면 grid는 두 방향 레이아웃 시스템
- grid container, grid item
### 컨테이너에 적용
- display: gird
- grid-template-rows/columns 그리드 행/열 크기를 지정. 
    - 크기를 나열함 1fr 1fr 1fr은 비율 대로 트랙의 크기를 나눠 1:1:1로 3개의 트랙을 만들겠다는 의미. 
    - repeat(5, 1fr 2fr 1fr) 함수를 사용하여 반복 가능. 
    - minmax(n, m)으로 최소 최대 길이 지정.
    - repeat(auto-fill, minmax(20%, auto)) row에는 5개 셀이 들어가는데 셀의 개수가 모자르면 공간이 남고 auto-fit을 사용하면 공간을 채워 늘림.
- row/column-gap / gap : 그리드 셀 사이의 간격
- grid-row/column: 시작/끝 셀 영역을 지정 2 / span 3으로 몇 개의 셀을 차지할 지 정하는것도 가능.
- grid template-areas: 각 영역에 이름을 붙이고 그 이름을 이용해서 배치
    - grid-area: name으로 이름 지정
- grid-auto-flow: 아이템이 자동 배치되는 흐름을 결정. dense로 빈 셀에 넣을 수 있음.
- align-items: 세로 축 방향 정렬
- justify-items: 가로 축 방향 정렬
- align-content: grid 아이템 모두 정렬
- justify-content: gird 아이템 모두 정렬
### 아이템에 적용
- *-self
- order

## 미디어 쿼리
- 미디어 유형과 미디어 특성으로 구성되는 참 또는 거짓의 값을 가지는 논리식
- 다양한 디바이스들이 웹브라우징을 지원하며 뷰포트 너비에 따라 유연하게 컨텐츠를 배치하는 기술이 중요해짐.
- 미디어 유형(스크린, tv, 프린터)과 미디어 특성(최소/최대 높이, 단말기 방향, 최소/최대 화면 비율)을 기반으로 동작
```css
    @media screen and (max-width: 768px) {
        body {
            background-color: blue;
        }
    }
```

## 가운데 정렬
### div
```css
    .pm {
        position: absolute;
        left: 0;
        right: 0;
        top: 0;
        bottom: 0;
        margin: auto;
    }

    .pt {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%, -50%);
    }

    .f {
        display: flex;
        justify-content: center;
        align-items: center;
    }
```
### text
```css
    div { 
        text-align: center; 
	    padding: 3em 0;
    }
```
### image
```css
    img { 
        vertical-align: middle;
    }
```

## 애니메이션
```css
    @keyframse fadeIn {
        0% { opacity: 0; }
        100% { opacity: 1; }
    }
    div {
        animation-name: fadeIn;
        animation-duration: 3s;
    }

    div {
        transition: transform 2s;
    }
    div:hover {
        transform: translateX(-50px);
    }
```
### css 애니메이션 vs js 애니메이션
- css
    - transition, animation 속성
    - 간단한 애니메이션 처리
    - 외부 라이브러리를 필요로 하지 않음
    - 메인스레드가 아닌 별도의 컴포지터 스레드에서 그려지기 때문에 효율적
- js
    - setInterval() / requestAnimationFrame() 사용
    - css로 처리하기에는 복잡한 애니메이션, 세밀한 구성
    - 외부 라이브러리로 성능 좋은 애니메이션 구현 가능
    - 브라우저 호환성 측면에서 transition/animation 보다 뛰어남

## Others
### calc
```css
    div {
        width: calc(100% - 400px);
    }
```
### appearance
운영체제 및 브라우저에 기본적으로 설정되어 있는 스타일
```css
    div {
	    appearance: none;
        -webkit-appearance: none;
    }
```
### outline
요소를 눈에 띄게 하기 위해 데두리의 바깥쪽에 그려지는 선
```css
    div {
	    outline: none;
    }
```
### var()
- CSS의 :root 의사클래스는 문서 트리의 루트 요소를 선택
```css
    :root {
        --main-bg-color: pink;
    }

    body {
        background-color: var(--main-bg-color, black);
    }
```

https://studiomeal.com/archives/197
https://studiomeal.com/archives/533