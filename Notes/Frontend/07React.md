## React
- 사용자 인터페이스를 만들기 위한 JavaScript 라이브러리
- MVC 애플리케이션의 View에 관련된 영역만 담당
- SPA을 전제로 하고 있음.
- 모듈형 개발으로 재사용이 필요한 기능을 언제든지 필요한 곳에서 호출하여, 반복적인 코드 작성 없이 사용할 수 있도록 함.
- 라이브러리로, 필요한 부분에만 적용 가능하여 기존 프로젝트에 리액트를 통합하기 쉽게 만들어줌.

### JSX
컴포넌트의 렌더링을 보다 직관적으로 이해할 수 있도록 도와줌.

### 가상 DOM
브라우저가 관리하는 실제 DOM이 아닌 가상 DOM을 사용하여 UI 업테이트를 처리함.
실제 DOM과 Virtual DOM의 차이점을 비교하고, 변경된 부분을 실제 DOM에 적용.
최소한의 DOM 조작이 가능하여 신속한 UI 업데이트를 가능하게하고 성능을 최적화 시킴.

### 단방향 데이터 흐름
데이터 변경이 UI로 전달되어 화면 업데이트, 성능의 저하 없이 DOM을 렌더링 시켜줌.

### 컴포넌트 기반 아키텍처
득정 기능을 수행하는 독립적인 단위인 컴포넌트를 이용해, UI 요소를 컴포넌트로 분리하여 개발하고 조합하여 복잡한 UI 구성 가능.
#### 컴포넌트 생명 주기
컴포넌트가 생성되고 사용되고 소멸될 때 까지 일련의 과정을 말함.
생명주기 안에서는 특정 시점에 자동으로 호출되는 메서드가 있음.
1. 마운트
    - React 엘리먼트를 DOM 노드에 추가할 때 발생하며 한 번만 실행
        1. constructor() 엘리먼트를 생성하여 기본 state와 props를 설정
        2. getDerivedStateFromProps()
        3. render() 로 컴포넌트를 DOM에 부착
        4. componentDidMount()
2. 업데이트
    - State나 Props가 변경되어 React 엘리먼트를 업데이트 할 때 발생, 여러번 실행
        1. getDerivedStateFromProps() props가 바뀌면 state를 바꿔줌
        2. shoouldComponentUpdate() false 리턴하면 render 취소 - 불필요한 재렌더링 막을 수 있다
        3. render()
        4. getSnapshotBeforeUpdate()
        5. ComponentDidUpdate()
3. 언마운트
    - React 엘리먼트를 DOM에서 제거할 때 발생하며 한 번만 실행
    - componentWillUnmount() 연결했던 이벤트 리스너를 제거하는 등의 활동

이렇게 클래스형 컴포넌트는 state관리와 라이프사이클 API를 사용할 수 있지만 

1. Hook이란 개념이 도입되면서 함수형 컴포넌트에서도 state관리와 라이프사이클 API를 심플하게 사용할 수 있음.
2. 마운트 속도도 render()가 필요없는 함수형 컴포넌트에 비해 느림
3. 가독성이 떨어짐.
4. this를 사용하므로 요청이 진행되고 있는 상황에서 컴포넌트 리렌더링 되면 props가 바뀌는 문제.

등의 문제로 함수형 컴포넌트 사용이 권장.

### 예시

```javascript
    import ReactDOM from 'react-dom';
    function App ({name}){
        return <h1>Hello, {name}!</h1>
    }

    ReactDOM.render(<App name="홍길동" />, document.getElementById('root'));

    const root = ReactDOM.createRoot(document.getElementById('root'));
    root.render(<App name="홍길동" />);
```

JSX 문법
```javascript
    function F({items}) {
        return React.createElement(
            'ul',
            { className: 'ul' },
            items.map((item, idx) => React.createElement('li', { key: i }, item))
        );
    }

    function F({items}) {
        return (
            <ul class='ul'>
                items.map((item, idx) => <li key={idx}>{item}</li>)
            </ul>
        )
    }
```

컴포넌트 최상위 노드를 둘 이상 지정 불가

### 프레임워크, 라이브러리
- 프레임워크
    - 개발을 위한 기본 구조와 규칙을 제공하는 도구. 개발자는 프레임워크가 제공하는 규칙과 인터페이스에 따라 코드 작성
    - 애플리케이션의 흐름과 제어를 관리하며, 필요한 기능과 도구 제공
- 라이브러리
    - 개발을 위해 재사용 가능한 코드의 집합. 특정 기능을 수행하는 함수, 클래스, 모듈로 구성
    - 개발자가 필요한 기능을 호출하여 사용
    - 개발자가 코드의 흐름과 제어를 직접 관리

https://www.elancer.co.kr/blog/view?seq=167
https://velog.io/@gyumin_2/React.js-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-%EC%83%9D%EB%AA%85%EC%A3%BC%EA%B8%B0Life-Cycle
https://github.com/Esoolgnah/Frontend-Interview-Questions/blob/main/Notes/important-3/react-life-cycle.md
