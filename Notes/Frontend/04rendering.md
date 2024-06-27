## 렌더링의 원리
브라우저가 화면에 나타나는 요소를 렌더링 할 때, 블링크, 웹킷, 개코 같은 렌더링엔진을 사용.
렌더링 엔진이 HTML, CSS, Javascript로 렌더링할 때 CRP라는 프로세스를 사용하며 다음 단계들로 이루어짐.

1. HTML을 파싱 후, DOM트리를 구축
2. CSS를 파싱 후, CSSDOM트리 구축
3. Javascript 실행
4. DOM과 CSSDOM을 조합하여 렌더트리를 구축 (화면에 보이지 않고 공간을 차지하지 않는 것은 랜더트리로 구축되지 않음)
5. 뷰포트 기반으로 렌더트리의 각 노드가 가지는 정확한 위치와 크기를 계산 (Layout)
6. 계산한 위치/크기를 기반으로 화면에 Paint

### CRP
Critical Rendering Path의 약자로 HTML, CSS, Javascipt를 화면에 픽셀로 변화하는 일련의 단계를 의미

### 파싱
하나의 프로그램을 런타임 환경(브라우저의 자바스크립트 엔진)이 실제로 실행할 수 있는 내부 포맷으로 분석하고 변환.
#### 자바스크립트 엔진이 코드를 실행하는 과정
- 소스코드를 파싱하여 Abstract Syntax Tree로 변환
- 인터프리터는 AST를 기반으로 바이트코드를 생성
- 인터프리터가 바이트 코드를 실행할 때, 자주 사용되는 함수 및 타입 정보 등이 있는 Profiling Data와 같이 최적화 컴파일러에게 보냄.
- 최적화 컴파일러는 프로파일링 데이터를 기반으로 최적화된 코드를 생성
- 프로파일링 데이터 중에 잘못된 부분이 있다면 최적화 해제(deoptimize) 작업을 하고 다시 바이트 코드를 실행.

### DOM
Documnet Object Model의 약자로 웹 페이지를 이루는 태그들을 자바스크립트가 이용할 수 있게끔 브라우저가 트리구조로 만든 객체 모델(html 태그 동적 제어). 최상위 인터페이스로 Node가 있음.
엘리먼트(<div>, <p>의 태그), Attribute(태그 안의 속성) 뿐만이 아닌 텍스트 노드와 주석 노드까지 포함.
브라우저가 html 페이지를 로드하는 과정에서 태그들을 각각의 객체로 만듬.
DOM을 다루기 위해 getElemnetsById, querySelector, firstElementChild 등과 같은 브라우저가 제공하는 DOM API 사용.

### BOM
Browser Object Model의 약자로 브라우저의 창이나 프레임을 제어할 수 있게 해주는 객체모델. 브라우저 새 창 열기, 다른 문서로 이동 등의 기능 수행 가능케함.
웹 페이지 내용을 제회한 웹 브라우저 창에 포함된 모든 객체 요소 의미함.
javascript의 최상위 객체인 window가 있고 하위 객체들로 location, document, history 등이 있음.

### CSSOM
CSS Object Model의 약자로 CSS 내용을 파싱하여 자료를 구조화 한 것으로 트리구조.

### 렌더트리
CSSOM과 DOM 트리의 결합으로 만들어짐. 웹 페이지에 나타낼 각 요소들의 위치를 계산하는데 사용됨.
Layout 단계는 렌더트리를 이용해 뷰포트 내에서 노드의 정확한 위치와 크기를 계산.
Paint 단계는 계산된 위치와 크기를 바탕으로 실제 픽셀로 변환하여 전달.

### Reflow
- DOM엘리먼트 추가, 제거, 변경
- CSS스타일 추가, 제거, 변경
- CSS3 애니메이션과 트랜지션 모든프레임에서 발생
- 유저 인터랙션 hover, input text, window resize

### Repaint
- 가시성이 변경 (opacity, background-color, visibility, outline)
- reflow 실행 후

https://velog.io/@imok-_/JavaScript-DOM-BOM-%EC%9D%B4%EB%9E%80
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/browser-rendering.md
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/bom-dom.md
https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-5/browser-rendering.md