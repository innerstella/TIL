## 상대 단위

- 고정되지 않고 어떤 기준에 따라 유동적으로 바뀔 수 있는 단위
- rem, em, % 등
- em, rem : css 상에서 font-size의 속성 값에 비례해서 결정됨
    <aside>
    💡 1rem의 기준을 어느 것으로 정하느냐의 차이
    </aside>

## `em`

> 상위 요소의 font-size \* em값 = px값

- 만약 해당 요소의 font-size가 없으면, 부모 요소의 글꼴 크기를 1em으로 사용함
- 중첩이 일어나면, 기준이 되는 font-size가 변함 (주의 🌟)

## `rem`

> 최상위 요소의 font-size \* rem값 = px값

- 중첩이 일어나더라도, 기준이 되는 font-size는 변하지 않음
- 사용자가 브라우저의 기본 font-size를 조절하더라도 작업한 레이아웃이 틀어지지 않게 반응함
- 브라우저에서 설정한 기본 font-size에 따라 크기가 변해야 하는 곳에 사용함

---

### 참고 자료

1. https://brunch.co.kr/@bommade/25
2. https://fromnowwon.tistory.com/entry/em-rem
