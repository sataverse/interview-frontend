## 모듈 시스템
목적이나 기능에 따라 코드를 분리

## 모듈 번들러
분리된 코드를 하나의 파일로 병합하는 개발 도구 - JS모듈, CSS 등을 브라우저에서 실행할 수 있는 단일 파일로 묶는데 사용

### 사용되는 이유
- 모든 브라우저가 모듈 시스템을 완전하게 지원하지 않음.
- 코드의 종속성 관계를 관리하는데 도움.
- 한 번의 요청으로 파일을 받아 로딩 속도에서의 이점.
- 개발과 빌드, 최적화를 위한 플러그인 제공

### 종류
- Webpack: 풍부한 생태계, 많은 서드파티를 필요로 하는 어플리케이션에서 유리
- Rollup: 최소한의 서드파티로 라이브러리를 만드는데 유리
- Pacel: 간단한 어플리케이션에 유리
- Vite: esbuild 번들링을 통해 개발 환경에서 높은 속도

https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/javascript/module.md
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/bundler-transpiler.md
https://enjoydev.life/blog/frontend/4-module-bundler