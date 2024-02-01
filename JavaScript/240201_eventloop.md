> 일반적인 작업은 Call Stack에서 이루어짐
>
> 시간이 소요되는 작업들(setTimeout, 이벤트, HTTP 요청 메서드 등)은 Web API에서 대기하다가 Callback Queue로 보내짐
>
> Call Stack이 비워져 있을 때만 Callback Queue에 저장되어있던 작업들을 Call Stack으로 보냄

## 이벤트 루프

- Call Stack이 다 비워지면 Callback Queue에 있는 함수를 하나씩 Call Stack으로 옮기는 역할

### Web API

- 브라우저에서 제공하는 API
  - DOM, Ajax, TimeOut 등
- Call Stack에서 실행된 비동기 함수는 Web API를 호출하고, Web API는 콜백 함수를 Task Queue에 넣음

## Call Stack

- 실행된 코드의 환경을 저장하는 자료구조
- 일반적인 작업은 콜 스택에서 이루어짐
- 함수가 실행되는 순서를 기억하고 있음
- 함수를 실행하려면, 스택의 가장 위에 해당 함수를 넣게 되고, 함수에서 리턴이 일어나면 스택의 가장 위쪽에서 함수를 꺼냄 (LIFO)
- 에러가 발생했을 때, 어떤 함수에서 에러가 발생했는지 보여주는 로그로 출력되는 것이 콜 스택의 값들
- stack overflow : 콜 스택이 가득 차서 발생하는 에러

## Callback Queue

- 함수를 저장하는 자료구조
- 가장 먼저 들어온 함수를 가장 먼저 처리 (FIFO)

```jsx
// 1번
let num = 1;

// 2번
setTimeout(() => {
  num = 2;
}, 0);

// 3번
num = 3;

// 4번
console.log(num);
```

위 코드를 실행하게 되면 콘솔에는 3이 출력된다.

- setTimeout은 동작하는 최소 시간을 보장한다
  - 정확히 얼마 후 동작하겠다는 의미가 아니라, 얼마 후 동작하는 최소 시간을 보장한다
  - 정해진 시간 후 콜백이 콜백 큐에 쌓이는데, 콜백 큐에 쌓인 콜백이 콜 스택에 들어오기 위해서는 콜 스택이 비어 있어야 함
  - 정해진 시간이 지난 후 그 이후에 콜스택이 비어있을 때 setTimeout 콜백이 실행됨
- 따라서 위 코드의 동작 순서를 작성해보자면,
  1. `num`에 `1`이라는 값이 할당된다
  2. `setTimeout` 함수는 Web API를 호출하고, Web API에서 setTimeout 작업이 완료되면, Callback Queue에 등록한다.
  3. `num`에 `3`이라는 값이 재할당된다
  4. 콘솔에 `3`이 출력된다
  5. 모든 실행을 마치면, 이벤트 루프가 돌아서 Callback Queue에 있던 함수를 Call Stack으로 가져와서 실행하고, `num`에는 `2`라는 값이 재할당된다.

---

### 참고 자료

1. https://beomy.github.io/tech/javascript/javascript-runtime/
