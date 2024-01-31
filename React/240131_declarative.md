# 선언형

## React

사용자 인터페이스를 구축하기 위한 선언적이고 효율적이며 유연한 JavaScript 라이브러리

컴포넌트라고 불리는 작고 고립된 코드의 파편을 이용하여 복잡한 UI를 구성하도록 도움

## 선언형

> React는 상호작용이 많은 UI를 만들 때 생기는 어려움을 줄여줍니다.
> `애플리케이션의 각 상태에 대한 간단한 뷰만 설계하세요.`
>
> 그럼 React는 데이터가 변경됨에 따라 적절한 컴포넌트만 효율적으로 갱신하고 렌더링합니다.
>
> 선언형 뷰는 코드를 예측 가능하고 디버그하기 쉽게 만들어 줍니다.

### 선언형 프로그래밍 (Declarative Programming)

(↔ 명령형 프로그래밍 (Imperative Programming))

원하는 결과를 묘사하는 방식으로 코드를 작성하는 프로그래밍 패러다임

‘데이터를 어떻게 조작해야 하는지’가 아니라, ‘원하는 데이터는 무엇인지’에 집중

전체적인 가독성과 추상화 수준을 높여 개발자가 문제의 본질에 집중할 수 있도록 도와줌

재사용성이 높고 병렬 처리가 유리한 특징을 가지게 됨

### 리액트 뷰 작성 방식

```jsx
const LoginForm = () => {
  return (
    <article>
      <p>ID</p>
      <input name="id" type="text" />
    </article>
  );
};
```

원하는 LoginForm의 모습(결괏값)만 return 하고 있으며, 어떻게 UI를 화면에 보이게 할 건지는 작성되어있지 않음

⇒ UI를 다루는 부분은 리액트에게 위임하고, 개발자는 결과에만 초점을 맞춰 개발할 수 있는 것

### 선언형 코드 작성을 위한 몇 가지 방법

1. 자바스크립트에서 제공하는 메서드 활용하기

   자바스크립트는 기본적으로 선언형 코드를 작성할 수 있는 메서드를 제공함

   - `map()`, `filter()`, `some()`, `every()`

2. Concurrent UI 패턴 사용

   조건부 렌더링이 필요할 때, Error Boundary와 Suspense를 사용한 제어의 역전을 통해 개선

   → 로딩 또는 에러 상태에 따른 렌더링 제어권을 부모 컴포넌트에게 전가하고, 현재 컴포넌트는 보여주고 싶은 것에만 집중

   → 컴포넌트는 본인의 역할에 따른 관심사만 집중할 수 있기 때문에 이해하기 쉬운 선언형 컴포넌트를 만들 수 있음

   → 복잡한 비동기 컴포넌트에서도 결과물에 집중할 수 있는 코드를 만들 수 있음

### 선언형의 장점

1. 코드가 간결해진다.
2. 무엇을 보여줄지에 집중할 수 있다.
3. 결과를 예측하기 쉬워진다.

---

### 참고 자료

1. https://ko.legacy.reactjs.org/
2. https://ko.legacy.reactjs.org/tutorial/tutorial.html
3. https://yozm.wishket.com/magazine/detail/2083/
4. [https://velog.io/@kairase024/리액트와-선언형-프로그래밍Declarative-Programming](https://velog.io/@kairase024/%EB%A6%AC%EC%95%A1%ED%8A%B8%EC%99%80-%EC%84%A0%EC%96%B8%ED%98%95-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8DDeclarative-Programming)
