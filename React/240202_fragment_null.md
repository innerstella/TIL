<aside>
❓ jsx에서 `null`, `undefined`, `fragment` 렌더링이 어떤 차이를 가지는 지 꼭 공부해보기

</aside>

## JSX는 `null`, `undefined`, `Fragment` 모두 반환할 수 있다

```jsx
{
  data ? <div>{data}</div> : <></>;
}
{
  data ? <div>{data}</div> : null;
}
{
  data ? <div>{data}</div> : undefined;
}
```

### 공통점

페이지에는 보이지 않는다

### Fragment

> 단일 엘리먼트가 필요한 상황에서 엘리먼트들을 `<Fragment>`로 묶어 함께 그룹화합니다. `<Fragment>`로 엘리먼트들을 그룹화하더라도 실제 DOM에는 아무런 영향을 주지 않으며, 그룹화하지 않은 것과 동일합니다.

- Fragment는 빈 태그이기 때문에, 실제로 렌더링을 하면 빈 태그는 사라진다. 이러한 특성은 레이아웃을 건드리지 않기 때문에 스타일링에 유용하다
- 하지만 화면에만 보이지 않을 뿐, **실제로는 렌더링 과정을 거친다.**
  - 최악

### null

- 값이 없는 상태로, 개발자가 명시해서 값을 초기화할 때 사용함
  - 권장
- 컴포넌트에서 null을 반환한다는 것 → 아무것도 렌더링하지 않겠다는 것
  - React는 이 컴포넌트와 그 안에 있을 수 있는 모든 자식 렌더링을 건너뜀
  - 특정 state나 props에 따라 컴포넌트를 조건부로 렌더링하고 싶을 때 유용할 수 있음

### undefeind

- 변수를 선언해서 초기화한 후에 할당하지 않았을 때, 함수의 기본 리턴값, 객체의 없는 프로퍼티를 참조할 때, 배열의 없는 인덱스를 참조할때 반환됨
- React 컴포넌트 자체에서 반환 값이 없을 때 기본적으로 사용된다

<aside>
❓ 아무것도 렌더링하지 않을 때 → `null`

엘리먼트를 그룹화할 때 → `fragment`

</aside>

---

### 참고 자료

1. https://velog.io/@yeomjung95/React-vs-null-vs-undefined
2. https://react-ko.dev/reference/react/Fragment#returning-multiple-elements
3. https://junghyeonsu.com/posts/react-fragment-vs-null/
4. [https://velog.io/@fromjjong/JSX에서의-nullundefinedfragment-3가지를-비교해보자](https://velog.io/@fromjjong/JSX%EC%97%90%EC%84%9C%EC%9D%98-nullundefinedfragment-3%EA%B0%80%EC%A7%80%EB%A5%BC-%EB%B9%84%EA%B5%90%ED%95%B4%EB%B3%B4%EC%9E%90)
5. https://onlydev.tistory.com/171
