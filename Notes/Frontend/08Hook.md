## Hooks
리액트 훅은 리액트 클래스형 컴포넌트에서 이용하던 코드(componentDidUpdate, componentWillUnmount 등)를 작성할 필요 없이 함수형 컴포넌트에서 다양한 기능을 사용할 수 있게 만들어준 라이브러리로 함수형 컴포넌트에서만 사용 가능.

## useState
함수형 컴포넌트에서도 가변적인 상태를 지니고 있을 수 있게 해줌.

## useEffect
리액트 컴포넌트가 렌더링 될 때마다 특정 작업을 수행하도록 설정 할 수 있는 Hook.
마운트 될 때만 실행하고 싶다면 두번째 파라미더로 비어있는 배열을 특정 값이 업데이트 될 때만 실행하고 싶으면 의존성 배열을 넣으면 됨.
컴포넌트가 언마운트 되기 전 혹은 업데이트 되기 직전에 어떠한 작업을 수행하고 싶다면 함수를 반환.

## useContext
Context를 보다 쉽게 사용 가능. context는 앱 안에서 전역적으로 사용되는 데이터를 여러 컴포넌트끼리 쉽게 공유하는 방법. 전역적인 데이터 전달.
```javascript
    const ThemeContext = createContext('black');
    const ContextSample = () => {
        const theme = useContext(ThemeContext);
    }
```

## useReducer
useState 보다 컴포넌트에서 더 다양한 상황에 따라 다양한 상태를 다른 값으로 업데이트하고 싶을 때 사용하는 Hook.
현재 상태와 업데이트를 위해 필요한 정보를 담은 액션 값을 전달 받아 새로운 상태를 반환하는 함수. 새로운 상태를 만들 때 불변성을 지켜야함.
첫번째 파라미터는 리듀서 함수 두번째 파라미터는 기본 값을 인자로 받음.
리턴하는 첫번째 값은 현재 가르키고 있는 상태, 두번째 값은 액션을 발생시키는 함수.
```javascript
    function reducer(state, action) {
        switch (action.type) {
            case 'INCREMENT':
                return { value: state.value + 1 };
            case 'DECREMENT':
                return { value: state.value - 1 };
            default:
                return state;
        }
    }

    const [state, dispatch] = useReducer(reducer, { value: 0 });
    const incr = () => dispatch({ type: 'INCREMENT' });
```

## useMemo
함수형 컴포넌트 내부에서 발생하는 연산을 최적화.
첫번째 인자로 함수, 두번째 인자로 의존성 배열을 넣으면 배열의 값이 변경되었을 때만 호출하도록 하고 함수의 리턴 값을 받음.
```javascript
    const avg = useMemo(() => getAverage(list), [list]);

    <div>평균 값: {avg}</div> 
```

## useCallback
이벤트 핸들러 함수를 필요할 때만 생성하여 렌더링 성능을 최적화.
컴포넌트 내부에 선언된 함수는 리렌더링 될 때마다 새로 생성되는데, 렌더링 해야 할 컴포넌트의 개수가 많아진다면 최적화 해주는것이 좋음.
첫번째 인자에는 생성할 함수를 두번째 인자에는 의존성 배열을 넣어줌.(빈 배열을 넣으면 마운트 될 때 한번만 함수 생성)
useMemo를 변형해 더 편하게 사용 할 수 있는 Hook
```javascript
    const f = useCallback(() => {
        console.log('hello world!');
    }, [a])
```

## useRef
함수형 컴포넌트에서 DOM 요소에 접근 할 수 있게 해줌.
컴포넌트 로컬 변수를 사용해야 할 때도 활용가능함. current로 값에 접근 또는 변경이 가능하며 ref안의 값은 바뀌어도 컴포넌트가 렌더링 되지 않음. 컴포넌트가 렌더링 되어도 Ref안에 저장되어 있는 값은 변화하지 않고 유지.
```javascript
    const ref1 = useRef(null);
    const ref2 = useRef(1);

    ref1.current.focus();
    ref2.current = 2;

    <input value={num} ref={ref1} />
```

## 함수형 컴포넌트의 생명주기
### 마운트
- constructor()
    - 컴포넌트가 호출 되면 가장 먼저 호출 되는 것은 컴포넌트 내부.
    - State를 정의하거나 사용될 함수들에 대해 미리 정의.
- render()
    - return()
    - 부모 컴포넌트로 전달받은 props와 컴포넌트 내부에서 정의한 state 값의 접근이 가능.
- componenDidMount()
    - useEffect(()⇒{}, [])
    - 컴포넌트 내에서 렌더링이 수행된 이후에 단 한번만 실행.
### 업데이트
- componentDidUpdate()
    - useEffect(()⇒{}, [value]), useEffect(()⇒{})
    - 값이 변경될 경우나, 리렌더링이 발생하는 경우 실행 (부모 컴포넌트가 리 렌더링, props 변화, state의 변경)
### 언마운트
    - useEffect(()⇒{ return () => {}}, [value])
    - 컴포넌트가 DOM에서 제거되기 직전에 호출
-componentWillUnmount()


https://velog.io/@velopert/react-hooks
https://adjh54.tistory.com/43