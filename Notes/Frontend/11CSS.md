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
### css vs js

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

