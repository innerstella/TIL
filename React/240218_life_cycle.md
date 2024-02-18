> 리액트는 컴포넌트에서 생명주기 메소드를 활용해 특정 시점에 코드를 실행할 수 있도록 지원하고 있습니다.

<aside>
💡 라이프 사이클을 고려하며 개발해야 한다

⇒ 리액트 애플리케이션을 안정적이고 효율적으로 만들기 위함

1. 컴포넌트 초기화
   - 컴포넌트의 상태 설정, 외부 데이터 가져와서 초기화할 떄 유용
2. 렌더링
   - UI를 업데이트하고 렌더링하기 전에 사전 작업 수행 가능
3. 상태 변화 감지 및 처리
   - 컴포넌트의 상태가 변경될 때 해당 변화에 대한 작업 수행 가능
   - 상태가 변경되면 UI를 업데이트하거나 상태 관련 로직 실행 가능
4. 컴포넌트 제거 - 컴포넌트가 더 이상 필요하지 않을 때 정리 작업 수행 가능 - 메모리 누수 방지, 리소스 해제
</aside>

### 클래스형 컴포넌트 생명주기

- 생성할 때
  - constructor : 컴포넌트의 생성자 메소드로, 가장 먼저 실행하는 메소드
  - getDerivedStateFromProps: props로 받아온 것을 state에 설정하고 싶을 때 사용
  - render : 컴포넌트를 렌더링하는 메소드
  - componentDidMount : 컴포넌트의 첫번째 렌더링이 마치고 나면 호출하는 메소드
- 업데이트
  - getDerivedStateFromProps : 컴포넌트의 props나 state가 바뀌었을 때도 해당 메소드를 호출
  - shouldComponentUpdate : 컴포넌트의 리렌더링 여부를 결정하는 메소드
  - render : 업데이트한 내용을 렌더링
  - getSnapshotBeforeUpdate : 컴포넌트에 변화가 일어나기 직전의 DOM에 있는 정보를 가져오고, 해당 메소드에서 반환하는 값은 componentDidUpdate에 인자로 전달됨
  - componentDidUpdate : 리렌더링을 마치고, 화면에 우리가 원하는 변화가 모두 반영되고 난 뒤 호출하는 메소드. 세번째 파라미터로 getSnapshotBeforeUpdate에서 반환한 값을 조회할 수 있음
- 제거
  - componentWillUnmount : 컴포넌트가 화면에서 사라지기 직전에 호출. setTimeout, setInterval 등을 사용한 것이 있다면 해당 메서드에서 clearTimeout, clearInterval 등으로 제거할 때 사용함

### 함수형 컴포넌트 생명주기

> 컴포넌트 생성 속도, 가독성, hook 활용 등의 이점이 있음
>
> 생명 주기 메서드 없음 (hook으로 대체)

- constructor : useRef 또는 useState를 활용해 생성할 떄 한 번만 동작하는 hook을 만들어 사용할 수 있음
- getDerivedStateFromProps : useState(initialState)에 초기 상태 값으로 props를 설정해서 사용
- render : 함수형 컴포넌트에서 return에 대응
- componentDidMount : useEffect
- shouldComponentUpdate : React.memo
- getSnapshotBeforeUpdate, componentDidUpdate : 변화 감지를 원하는 props, state를 useEffect deps로 설정하여 사용
- componentWillUnmount : useEffect에 callback을 return해서 사용
