## 모듈
여러 기능들에 관한 코드가 모여있는 하나의 파일
목적이나 기능에 따라 코드를 분리

### 사용되는 이유
- 유지보수성: 기능들이 모듈화가 잘 되어있다면, 의존성을 줄일 수 있기 때문에 수정에 용이
- 네임스페이스화: 자바스크립트의 전역변수에 대한 겹치는 네임스페이스가 많아지는 현상을 해결
- 재사용성: 똑같은 코드를 반복하지 않고 모듈을 분리시켜서 필요할 때마다 사용

### CommonJS
node.js, Babel같이 ES6코드를 변환해주는 도구를 사용할 수 없으면 require 키워드 시용
```
const func = () => {};
modul.exports = { func };

const a = require('./a.js');
a.func();
```

### AMD
비동기 모듈에 대한 표준안들 다룬다. 브라우저 쪽에서 더 큰 효과를 발휘한다.

### UMD
CommonJS와 AMD를 통합하기 위한 패턴

### ES6
Bable을 통해 변환시켜 사용하여야 함.
as로 다른 이름으로 사용할 수 있고 *로 한번에 불러오거나 내보낼 수 있음.
```javascript
const A = () => {};
export default A;

export const B = () => {};

import A from 'moduleA';
import { B } from 'moduleB';
```

## 모듈 번들러
분리된 코드를 하나의 파일로 병합하는 개발 도구 - JS모듈, CSS 등을 브라우저에서 실행할 수 있는 단일 파일로 묶는데 사용
각각의 모듈 의존성을 해결함

### 사용되는 이유
- 모든 브라우저가 모듈 시스템을 완전하게 지원하지 않음.
- 코드의 종속성(의존성) 관계를 관리하는데 도움. 순서처리.
- 한 번의 요청으로 파일을 받아올 수 있어 로딩 속도에서의 이점. 모듈이 많아질수록 HTTP요청이 증가하는데 오버헤드 해결.
- JS압축, CSS전처리기 변환과 같은 작업 등을 자동화
- 개발과 빌드, 최적화를 위한 플러그인 제공

### 종류
- Webpack: 풍부한 생태계, 많은 서드파티를 필요로 하는 어플리케이션에서 유리. 소스코드와 모든 종속 관계의 모듈을 번들링 한 후 서버 준비.
- Rollup: 최소한의 서드파티로 라이브러리를 만드는데 유리
- Pacel: 간단한 어플리케이션에 유리
- Vite: esbuild로 미리 번들링한 모듈을 필요할 때 동적으로 가져오기 때문에 개발 환경에서 높은 속도

## 트랜스파일러
트랜스파일링이란 특정 언어로 작성된 코드를 비슷한 다른 언어로 변환시키는 행위이며 이를 해주는 것이 트랜스파일러. 호환성 증가.
모듈 번들러에 트랜스파일러를 추가해서 사용함

### 사용되는 이유
- 모든 브라우저가 ES6+의 기능을 제공하지 않기 때문에 ES5 코드로 변환시키는 과정이 필요
- React의 JSX 또는 TypeScript 코드를 자바스크립트 코드로 변환 (JSX란 JS에서 XML을 추가한 확장형 문법으로 직관적으로 UI 작업이 가능케함)
- Bable(Polyfill 역할도 하며 브라우저가 지원하지 않는 코드를 지원 가능하도록 수정하거나 새로 구현, 구현이 누락된 부분의 기능을 메꿔주는 역할) TypeScript Transpiler 

https://velog.io/@ssulv3030/%EB%AA%A8%EB%93%88-%EB%B2%88%EB%93%A4%EB%9F%AC%EB%9E%80webpack-pacel-rollup-%EB%B9%84%EA%B5%90
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/javascript/module.md
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/bundler-transpiler.md
https://enjoydev.life/blog/frontend/4-module-bundler