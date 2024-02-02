## DOM (Document Object Model)

- 객체로 문서 구조를 표현하는 방법으로 XML이나 HTML로 작성함
- 웹 브라우저는 DOM을 활용하여 객체에 자바스크립트와 CSS를 적용하며, DOM은 트리 형태이기 때문에 특정 노드를 찾거나 수정하거나 제거하거나 원하는 곳에 삽입할 수 있음

### DOM은 느릴까?

- DOM의 문제점 : 동적 UI에 최적화되어 있지 않음
- DOM 자체를 읽고 쓸 때의 성능은 자바스크립트 객체를 처리할 때의 성능과 비교하여 다르지 않음
- 웹 브라우저 단에서 DOM에 변화가 일어나면 웹 브라우저가 CSS를 다시 연산하고, 레이아웃을 구성하고, 페이지를 리페인트하는데, 이 과정에서 시간이 허비됨
  → DOM을 조작할 때마다 엔진이 웹 페이지를 새로 그리기 때문에, 업데이트가 너무 잦으면 성능이 저하될 수 있음

### 해결법

- DOM을 최소한으로 조작하여 작업을 처리
  → 리액트는 Virtual DOM 방식을 사용하여 DOM 업데이트를 추상화함으로써 DOM 처리 횟수를 최소화하고 효율적으로 진행함

## Virtual DOM

!https://res.cloudinary.com/practicaldev/image/fetch/s--NCIpFhXv--/c_limit,f_auto,fl_progressive,q_auto,w_800/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/02llb1lq9vc25v7l8dfb.PNG

- 실제 DOM에 접근하여 조작하는 대신, 이를 추상화한 자바스크립트 객체를 구성하여 사용함
- 리액트에서 데이터가 변하여 웹 브라우저에 실제 DOM을 업데이트할 때는 다음 3가지 절차를 밟음
  1. 데이터를 업데이트하면 전체 UI를 Virtual DOM에 리렌더링함
  2. 이전 Virtual DOM에 있던 애용과 현재 내용을 비교함
  3. 바뀐 부분만 실제 DOM에 반영함

### 장점

1. 성능 : 실제 DOM 조작을 최소화하고, 변경된 부분만 실제 DOM에 적용
2. 일관성 : 상태 변화를 추적하고, 적절한 타이밍에 변경 사항을 적용하여 렌더링 일관성을 유지
3. 복잡한 UI 관리
4. Cross-Platform 지원 : Virtual DOM은 독립적인 방식으로 동작하므로, React Native와 같은 플랫폼에서도 활용될 수 있음

### 단점

1. 추가적인 메모리 사용 : Virtual DOM은 메모리 상에 DOM과 완전히 동일한 구조의 메모리를 유지함
2. 복잡성 증가 : 애플리케이션의 뷰와 상태 동기화를 위한 추가적인 추상화 계층 사용
3. 특정 상황에서의 불필요함 : 정말 간단한 UI나 작은 규모의 어플리케이션에서는 불필요할 수 있음

---

### 참고 자료

1. 리액트를 다루는 기술
2. [https://velog.io/@dongjun187/React-Virtual-DOM-기초-동작-원리](https://velog.io/@dongjun187/React-Virtual-DOM-%EA%B8%B0%EC%B4%88-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC)
3. https://dev.to/adityasharan01/react-virtual-dom-explained-in-simple-english-10j6
