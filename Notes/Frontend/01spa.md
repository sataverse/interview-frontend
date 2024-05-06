## SPA vs MPA
### SPA
Single Oage Application의 약자로 하나의 HTML 파일을 기반으로 자바스크립트를 이용해 동적으로 화면의 컨텐츠를 바꾸는 방식의 웹 어플리케이션이다.
다수의 페이지를 표시할 때 페이지 전환을 수행하지 않는다.
변경될 부분만 동적으로 업데이트한다.
클라이언트 사이드 라우팅 라이브러리, 전역 상태관리 라이브러리 사용.
웹 팩 등을 이용하여 번들링 작업을 수행한 후 빌드 된 웹 어플리케이션 배포
Gmail, Facebook, Netflix

### MPA
Multiple Page Application의 약자로 사용자가 페이지를 요청할 때마다, 웹 서버가 요청한 데이터를 HTML로 파싱해서 보여주는 방식의 웹 어플리케이션이다.

## CSR vs SSR
### CSR
브라우저가 서버에게 HTML과 JS파일(모든)을 요청한 후 로드되면 사용자의 상호작용에 따라 JS를 이용하여 동적으로 렌더링을 시킨다. 
#### 장점
- 첫 로딩만 기다리면, 동적으로 빠르게 렌더링 되므로 UX가 좋음.
- 서버의 부하가 적음.
- 비동기 방식의 업데이트로 동적 요소가 많은 웹 앱을 만들 때 유용.
#### 단점
- 모든 스크립트 파일이 로드될 때 까지 대기해야 함.
- 검색엔진 최적화(Search Engine Optimization)의 문제가 있음.
#### 해결방안
- 코드 스플리팅: 애플리케이션을 여러 청크로 분할하여 필요 부분만 로드하면 초기 로딩 시간이 단축
- 메타태그 또는 선택적 SSR: 크롤링의 어려움 개선.

### SSR
브라우저가 페이지를 요청할 때마다 해당 페이지에 관련된 파일 및 데이터를 받아와 렌더링.
#### 장점
- 페이지별로 분할되어 전송되므로 첫 페이지의 로딩 속도가 빠름
- 검색엔진 최적화가 가능.
#### 단점
- 매번 페이지를 요청할 때마다 새로고침 되므로 좋지 않은 UX (느린 페이지 전환)
- 큰 서버의 부하
- 페이지 전환시의 깜빡임.

https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/csr-ssr.md
https://www.elancer.co.kr/blog/view?seq=214