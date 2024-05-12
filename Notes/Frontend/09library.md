## React-Router-Dom
React로 생선된 SPA 내부 페이지 이동이 가능하도록 만들어주는 라이브러리.

a 태그를 사용하면 페이지 전체가 새로 로딩되므로 화면 깜빡임이 필수, 이는 UX를 떨어뜨리는 큰 요인.

SPA 안에서 모든 페이지를 렌더링해주면?
- 특정 페이지의 즐겨찾기 불가
- 뒤로가기 불가
- 새로고침 불가

```javascript
    const Router = () => {
        return (
            <BrowserRouter>
                <Routes>
                    <Route path="/" element={<Main />} />
                    <Route path="/search" element={<Search />} />
                    <Route path="/detail/:id" element={<Detail />} />
                    <Route path="/about/*" element={<About />}>
                        <Route path="history" element={<History />} />
                        <Route path="services" element={<Services />} />
                    </Route>
                    <Route path="*" element={<Error />} />
                </Routes>
            </BrowserRouter>
        );
    };

```

### BrowserRouter
- history API를 활용해 history 객체 생성
- history API는 사용자가 방문한 url 기록들을 스택 형태로 저장.
- 라우팅을 진행할 컴포넌트 상위에 BrowerRouter 컴포넌트를 생성하고 감싸주어야함.

### Route
- 현재 브라우저의 location 상태에 따라 다른 element 렌더링
- path에 매칭된 element 렌더링

### Routes
- 모든 Route의 상위 경로에 존재해야 하며 location 변경 시 하위에 있는 모든 Route 조회해 현재 location과 맞는 Route를 찾아줌.

### 중첩 라우팅
- 페이지 내에서 하위 페이지 만들 수 있고, 해당 페이지마다 경로를 이용한 데이터 전달도 가능
- 부모 요소에서 하위 라우팅 발생 시 컴포넌트를 렌더링 할 자리를 명시해야함. Outlet 컴포넌트 사용.

### Link
- 라우터 내에서 직접적으로 페이지 이동을 하고자 할 때 사용.
- 계층 구조에 상대적이므로 ./ ../ 같은 표현도 사용이 가능.
- useLocation 훅과 연계하여 특정 state를 넘겨주는 것도 가능.
```javascript
    <Link to="new-path" state={{ some: "value" }} />

    let { state } = useLocation();
```

### useNavigate
- 특정 이벤트가 발생했을 때 페이지 이동.
- 두번째 인자로 { replate: true } 설정하면 이동 후 뒤로가기 불가.
- state 전달 가능
```javascript
    navigate("/", { state: { cardId: cardId } });
    
    const location = useLocation();
    const { cardId } = location.state;
```

### useLocation
```javascript
    const { pathname, search, state } = useLocation();
```

### useParams
- url 파라미터는 http://naver.com/news/1234 의 1234 부분에 해당
- useParams Hook을 통해 추출하고 사용
```javascript
    let { id } = useParams();
```

### useSearchParams
- http://naver.com/search?word=abc&sort=1
- 쿼리 스트링을 추출하는 데 사용.
```javascript
    const [serchParams, setSearchParams] = useSearchParams();

    searchParams.get(key);
    searchParams.set(key, value);
    searchParams.append(key, value);
    setSearchParams(searchParams);
```

## Styled Components
- CSS in JS는 스타일 정의를 CSS 파일이 아닌 JS로 작성된 컴포넌트에 바로 삽입하는 스타일 기법. 한 컴포넌트에서 Document 구조와 스타일을 동시에 확인이 가능.
- 템플릿 리터럴을 사용하기 때문에 함수를 포함시킬 수 있음. 이를통해 가변적 스타일링이 가능함.
- 컴포넌트 밖에 지정해야함.

### 주요 문법
- &:hover, &:first-child같이 자신을 나타내는 &연산자
- 확장 및 상속
```javascript
    const Child = styled(Parent)`
        width: 500px;
    `
```
- css props
```javascript
    const css1 = css`
        ...
    `
    const Button = styled.button`
        color: black;
        ${css1}
    `
```
- attrs 속성지정
    - HTML tag가 갖고있는 고유의 attribute를 넣어 재사용하기 위한 컴포넌트를 만들 때 유용. 
    - attribute의 스타일 속성을 이용하면 in-line style로 적용되어 공통적인 부분을 계속 재생성할 필요없음. 
    - 자주 스타일이 변경되는 작업에 사용하면 효율적인 메모리 사용이 가능.
```javascript
    const Input = styled.input.attrs(props => ({
        type: 'password',
        color: 'blue',
        style: {
            marginBottom: props.marginbottom
        }
    }))`
        width: 500px;
        color: ${({ color }) => color};
    `
```
- 애니메이션
```javascript
    const rotate = keyframes`
        ...
    `
    const Button = styled.button`
        animation: ${roate} 2s linear infinite;
    `
```

## Zustand
- 단순화된 Flux 원리를 사용하는 작고 빠르며 확장 가능한 상태 관리 솔루션.
- 상태가 변경되면 불필요한 리렌더링을 일으키지 않음.
```javascript
    const sortStore = create(set => ({
        sort: 0,
        setSort: num => set({ sort: num }),
        increaseSort: () => set((prev) => ({
            sort: prev.sort + 1
        }))
    }));
    export const useSort = () => {
        const sort = filterStore(state => state.sort);
        const setSort = filterStore(state => state.setSort);
        return { sort, setSort };
    }
```
### 전역 상태 관리
- 여러 컴포넌트에서 공유해야 하는 상태를 한곳에서 중앙 집중적으로 관리하는 것.
- 데이터 일관성, 상태 관리 로직을 한 곳에서 관리하므로 쉬운 재사용, 유지보수의 용이
- props 전달, callback 함수를 통해 상태를 관리하면?
    - Props Drilling: 상태를 가장 하위 컴포넌트에 전달한다면 사용할 필요가 없는 중간 컴포넌트들을 커져야 함.
    - 데이터 일관성: 여러 컴포넌트에서 관리하면 일관성 유지가 어려움.
- 사용자 인증 정보(토큰), 앱 설정, 캐시된 데이터, 알림, 쇼핑 카트 등 전역 상태로 관리함.



https://velog.io/@kandy1002/React-Router-Dom-%EA%B0%9C%EB%85%90%EC%9E%A1%EA%B8%B0
https://velog.io/@hwang-eunji/Styled-Components-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%8A%A4%ED%83%80%EC%9D%BC-%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8
https://velog.io/@river-m/%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%A0%84%EC%97%AD-%EC%83%81%ED%83%9C-%EA%B4%80%EB%A6%AC
https://velog.io/@yeonsubaek/React-Zustand%EB%A1%9C-%ED%8E%B8%EB%A6%AC%ED%95%98%EA%B2%8C-%EC%83%81%ED%83%9C%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0