## REST
Representational State Transfer의 약자로 전반적인 웹 어플리케이션에서 상호작용하는데 사용되는 웹 아키텍쳐 모델.
HTTP URI를 통해 자원을 명시하여, HTTP Method(POST, GET, DELETE, PUT)를 통해 해당 자원에 대한 CRUD연산을 적용하는 것.
### 특징
- 서버 클라이언트 구조: 독립적인 동작
- Stateless: 클라이언트를 고려하지 않고 API요청에 대해서만 처리한다는 것으로구현이 간결해지는 장점이 있음
- 캐시 처리 가능: HTTP 표준을 기반으로 만들어져서 캐싱을 사용할 수 있음. REST API를 활용하여 GET 메소드를 Last-modified 값과 함께 보낼 경우 바뀐게 없다면 캐시된 값을 사용. 네트워크 응답시간 뿐만 아니라 API서버에 요청을 발생시키지 않기 때문에 부하가 덜함.
- 계층화 구조: 보안/로드 밸런싱/암호화 등을 추가할 수 있고 Proxy 및 게이트웨이 등의 중간매체 사용 가능.
- 인터페이스 일관성: HTTP의 표준만 따른다면 플랫폼이나 언어의 제약에 구애받지 않고 사용 가능
#### 장점
- 명확한 서버와 클라이언트 분리
- 쉽게 파악할 수 있는 REST API 메시지의 의도
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용 가능
- HTTP 프로토콜의 인프라를 그대로 사용해 별도의 인프라 구축 필요 없음
#### 단점
- 제한적인 HTTP Method 형태
- 호환 되지 않은 브라우저가 존재
### URI
Uniform Resource Identifier는 리소스를 식별하는 고유한 문자열 시퀀스
aaa.co.kr은 리소스의 이름만 나타내기 때문에 URI (Host + Path)
### URL
Uniform Resource Locator은 네트워크상에서 리소스의 위치를 나타내기 위한 규약
자원 식별자 + 위치, URL은 URI의 일종
https://aaa.co.kr은 위치(프로토콜)까지 나타내기 때문에 URL (Scheme + Host + Path)
### URN
리소스를 유일하고 영구적인 이름으로 식별

## API
Application Programming Interface의 약자로 응용프로그램에서 사용할 수 있도록 운영 체제나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스
프로그램끼리 통신할 수 있도록 하는 중재자

## REST API
REST 원칙을 적용하여 서비스 API를 설계한 것
### 올바른 규칙
- 소문자 사용
- 마지막에 슬래시 포함x
- 언더바 대신 하이픈
- 파일확장자 포함x
- 행위 포함x, HTTP Method로 표현
- 요청에 대한 응답의 상태코드를 명확하게 돌려주어야 함
    - 2xx: 성공 (200 Ok, 201 Created)
    - 3xx: 리다이렉션 (304 Not Modified)
    - 4xx: 클라이언트 에러 (401 권한없음, 403 금지, 404 not found)
    - 5xx: 서버 에러

## RESTful
REST API의 설계 규칙을 올바르게 지킨 시스템. 
모든 CRUD 기능을 POST로 처리하는 API는 REST API지만 RESTful하지 못함.

https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80
https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-5/rest-api.md
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/network/rest-api.md