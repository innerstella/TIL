## 객체 타입 타이핑

- `object`
  - 자바스크립트 객체의 정의에 맞게 대응하는 타입 시스템
  - 가급적 사용하지 말도록 권장됨
    - any 타입과 유사하게 객체에 해당하는 모든 타입 값을 유동적으로 할당할 수 있어 정적 타이핑의 의미가 크게 퇴색되기 때문임
- 객체를 타이핑하기 위해서는 타입스크립트에서만 독자적으로 사용할 수 있는 키워드를 사용하는게 일반적임
  - `type`
  - `interface`

```tsx
type NoticePopupType = {
	title: string;
	description: string;
};

interface INoticePopup {
	title: string;
	description: string;
};

const noticePopup1: NoticePopupType = { ... };
const noticePopup2: INoticePopup = { ... };
```

- 타입스크립트에서는 일반적으로 변수 타입을 명시적으로 선언하지 않아도 컴파일러가 자동으로 타입을 추론한다.
  - 모든 변수에 타입을 일일이 명시적으로 선언할 필요는 없음
  - 하지만 타입 추론에 대해서는 다양한 의견이 존재하고 개인의 취향 또는 팀의 컨벤션에 따라 다를 수 있음

## type vs interface 사례

<aside>
⭐ 공식 문서

- type : 작은 범위 내에서 한정적으로 사용
- interface : 전역적으로 사용할 때
</aside>

1. 대부분의 상황에서는 interface, 간단한 용도로는 type
2. type은 어떤 값에 대한 정의같이 정적으로 결정되어 있는 것, interface는 확장될 수 있는 basis를 정의하거나 어떤 객체 구성을 설명하는 요소
3. 선언 병합이 필요할 때는 interface, computed value를 사용해야 한다면 type
4. 객체 지향적으로 코드를 짤 때, 특히 상속하는 경우에는 interface 사용
5. union이나 intersection 처럼 type 정의에서만 쓸 수 있는 기능을 활용할 때 type 사용
6. 같은 속성을 공유하는 기준 인터페이스를 정의하고 확장할 때 interface 사용
