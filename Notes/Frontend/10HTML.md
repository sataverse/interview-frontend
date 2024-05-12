## HTML
Hyper Text Markup Language의 약자로 웹페이지의 구조와 내용을 담당.
### HTML5
- 클라이언트와 서버와의 통신이 가능해져 외부 응용프로그램을 사용하지 않을 수 있음. (ActiveX)
- 웹 브라우저의 비호환성 해결
- 웹 소켓, 웹 스토리지, 캔버스, 위치정보, 오프라인 웹 어플리케이션 지원

## DOCTYPE
- Document Type의 약자로 HTML이 어떤 버전으로 작성되었는지 미리 선언하여 웹 브라우저가 내용을 올바로 표시할 수 있도록 해주는 것.
- DOCTYPE을 가지고 있지 않은 HTML 문서는 브라우저가 호환 모드로 렌더링을 하고, 가지고 있으면 DOCTYPE에 맞게 표준 모드로 렌더링함.
- <!DOCTYPE html>로 선언하는 것이 가장 바람직

## data- 속성
- DOM에 데이터를 저장할 수 있는 사용자 정의 데이터 속성.
- 웹페이지가 독자적으로 사용하는 값이고 독립적인 소프트웨어가 이 속성을 사용해서는 안됨.

## head
- head: <title>, <meta>본문의 설명 name content의 쌍, <script>, <style>, <link href type rel>
- body: 문서의 본문 텍스트, 이미지, JS코드 등

## 웹 폼
- 웹페이지를 통해 사용자 입력을 받는 폼. name, method, action 속성을 가짐.
- action 속성은 폼 데이터를 처리할 웹 서버 응용프로그램을 지정.
- <input type='text' list='what'><datalist id='what'><option value='a'>
- <input type='radio' name='category' value='1'>
- <select name='category'><option value='1'>
- <label> 캡션

## script
### <script>
HTML 파싱이 중단되고 즉시 스크립트가 로드되며 로드된 스크립트가 실행되고 파싱이 재개
### <script async>
HTML 파싱과 병렬적으로 로드가 되는데, 스크립트를 실행할 때는 파싱이 중단.
### <script defer>
HTML 파싱과 병렬적으로 로드가 되는데, 파싱이 끝나고 스크립트를 로드.
### HTML 렌더링 중에 JavaScript가 실행되면 렌더링이 멈추는 이유
- 렌더링 엔진은 HTML 한 줄씩 순차적으로 파싱하며 DOM을 생성해 나가다가 JavaScript를 만나면 DOM 생성을 임시 중단.
- 자바스크립트 코드를 파싱하기 위해 자바스크립트 엔진에 제어권을 넘기게 됨.
- 파싱이 끝나면 다시 렌더링 엔진에 제어권을 넘겨 중단된 부분부터 HTML 파싱을 재개하며 DOM 트리를 생성.

## 시맨틱 마크업
- 의미를 잘 전달하도록 HTML 문서를 작성하는 것. 즉 각 태그를 그 용도에 맞게 사용해야 함.
    - 메인 컨텐츠에 <main>과 <section>, 독립적인 컨텐츠에는 <article>
    - CSS 스타일을 명시하는 태그는 적합하지 않음. <b> vs <strong>
- 검색엔진이 시맨틱 태그를 중요한 키워드로 간주하기 때문에 검색엔진 최적화(SEO)에 유리
- 단순한 div, span으로 둘러싸인 요소들보다 코드를 볼때 가독성이 좋음

## local storage vs session storage vs cookie
- 클라이언트 상에서 key/value 쌍을 저장할 수 있는 메커니즘
- 다른 도메인에서 접근 불가

### 쿠키
- 서버와 클라이언트가 주고 받은 내역을 기억하고 불러올 수 있는 역할
- Third Party Cookie 처럼 다른 도메인에 요청이 필요할 때 사용할 수 있음.
- 클라이언트의 HTTP요청 -> 서버 응답에 쿠키 생성해 전달 -> 클라이언트는 매 요청시 쿠키 HTTP Header에 담아 전송.
- 다시 보지 않은 팝업창, 로그인 자동 완성.
- 장점
    - 대부분의 브라우저가 지원
    - JS에서 쿠키 접근 불가하도록 옵션 설정할 수 있어 XSS로 부터 안전
- 단점
    - 적은 용량
    - HTTP 요청시 같이 전달되어 서버에 부담
    - 암호화 X
    - CSRF 위협에 취약(사용자 요청을 가로채서 변조)

### 웹 스토리지
- 클라이언트에 데이터를 저장할 수 있도록 HTML5부터 나온 데이터 저장소
- window 객체의 프로퍼티로 존재
- 장점
    - 서버에 불필요한 데이터를 저장하지 않음
    - 넉넉한 용량
    - 도메인 단위로 접근이 제한되는 CORS 특성 덕분에 CSRF로 부터 안전
- 단점
    - HTML5 지원하는 브라우저만 사용
    - XSS로 부터 위험. 로컬 스토리지에 접근하는 JS코드로 쉽게 접근
- 로컬 vs 세션
    - 로컬스토리지는 데이터 영구 저장, 세션 스토리지는 탭이 닫히면 초기화(일회성 로그인, 장바구니)

https://velog.io/@hs0217/%EC%BF%A0%ED%82%A4-%EB%A1%9C%EC%BB%AC-%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80-%EC%84%B8%EC%85%98-%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/html/semantic.md
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/html/doctype.md
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/html/data.md
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/html/script-tag-type.md
https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-3/why-stop-rendering.md