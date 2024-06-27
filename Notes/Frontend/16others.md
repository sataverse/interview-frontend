## JQuery
HTML 속 클라이언트 사이드 스크립트 언어(JS)를 단순화하도록 설계된 JS라이브러리.
엘리먼트를 쉽게 찾고 조작할 수 있으며 애니메이션 등 다양한 기능 제공.
브라우저 호환성이 있음.
사용자 조작에 맞춰 동적으로 변화하는 대화형 웹을 구현하기 위해서 돔 조작이 필요한데, 이로인해서 브라우저 성능이 낮아지는 문제가 있음.
```javascript
document.querySelector('.someDiv').innerHTML = 'some'; //Vanilla
$('.someDiv').html('some'); //JQuery
```

## CI와 CD
### CI(Continuous Integration)
- 빌드와 테스트를 자동화해서 공유 저장소에 병합시키는 프로세스
### CD(Continuous Deliver)
CI의 빌드/테스트를 통해서 정상적으로 수행됨을 확인하면 배포

## Node.js
- Chrome V8 JavaScript 엔진으로 빌드된 자바스크립트 런타임. (프로그램들을 실행할 수 있는 환경)
- 웹에서만 작동했던 자바스크립트를 어디서든 구동 가능하게 함. 무엇이든 자바스크립트로 만들 수 있음
- 기존에는 자바스크립트를 인터넷 브라우저 위에서만 해석(브라우저에 JS 엔진이 있음)

### Node.js 서버
- Non-blocking I/O 덕분에 채팅이나 SNS 처럼 요청이 많은 서비스에 사용
- 스레드 하나에서 처리되기 때문에 CPU연산이 많이 필요한 이미지/비디오 처리, 대규모 데이터 처리 서버로는 적절하지 않음

## JSON

## 함수 표현식 vs 화살표 함수 vs ...