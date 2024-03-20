## 제네릭

```tsx
type ExampleArrayType<T> = T[];

const array: ExampleArrayType>string> = ['a', 'b', 'c'];
```

- 정적 언어에서 다양한 타입 간에 재사용성을 높이기 위해 사용하는 문법
- 사전적 의미 : 특징이 없거나 일반적인 것
- @타입스크립트 : 일반화된 데이터 타입
  - 내부적으로 사용할 타입을 미리 정해두지 않고 타입 변수를 사용해서 해당 위치를 비워 둔 다음에, 실제로 그 값을 사용할 때 외부에서 타입 변수 자리에 타입을 지정하여 사용하는 방식
- 장점
  - 재사용성 향상 : 여러 타입에 대해 하나하나 따로 정의하지 않아도 되기 때문
- 주의할 점
  - tsx 파일에서 화살표 함수에 사용하면 에러 발생함
    - tsx = ts + jsx
    - 제네릭의 꺽쇠 기호와 태그 꺽쇠 기호 혼동
    - 대처 : 제네릭 부분에 `extends` 키워드를 사용
    - 보통은 function 키워드로 사용한다.
  ```tsx
  const arrowFunction = <T extends {}>(arg: T): T[] => {
    return;
  };
  ```

### 제네릭 vs any

ex) 배열

- 제네릭 : 배열 요소가 전부 동일한 타입이라고 보장 가능
- any : 배열 요소들의 타입이 전보 같지 않을 수 있음
  - any : 타입 정보를 잃어버린다고 생각해도 됨
  - 모든 타입을 허용하기 때문에 사실상 자바스크립트랑 다를 바가 없음

### 제네릭 예시

- 현업에서는 `API 응답 값의 타입을 지정할 때` 가장 많이 활용함
  ```tsx
  export interface MobileApiResponse<Data> {
    data: Data;
    statusCode: string;
    statusMessage?: string;
  }

  export const fetchPriceInfo = (): Promise<MobileApiResponse<PriceInfo>> => {
    const priceUrl = "https://~";

    return request({
      method: "GET",
      url: priceUrl,
    });
  };
  ```
- 제네릭을 굳이 사용하지 않아도 되는 타입
  - 타입 매개 변수를 그대로 선언하는 것 같은 기능을 할 때
  - 목적의 의미를 정확히 담고 있지 않을 때
- 너무 과하게 사용하면 가독성을 오히려 해친다.
  - 복잡한 제네릭은 의미 단위로 분할해서 사용하자
