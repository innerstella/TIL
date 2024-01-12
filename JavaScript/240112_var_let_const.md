JavaScript에서 변수를 선언하는 데 사용되는 키워드

|          | var       | let             | const           |
| -------- | --------- | --------------- | --------------- |
| 재선언   | o         | x               | x               |
| 재할당   | o         | o               | x               |
| 스코프   | function  | block           | block           |
| 호이스팅 | undefined | reference error | reference error |

## `var`

- ES5까지의 JavaScript에서 사용되는 변수 선언 키워드
- 선언과 초기화가 동시에 이루어지기 때문에, 호이스팅 시 undefined

## `let`

- ES6부터 도입된 블록 스코프를 갖는 변수 선언 키워드
- 선언 단계만 호이스팅되기 때문에, reference error 발생

## `const`

- ES6부터 도입된 블록 스코프를 갖는 변수 선언 키워드
- 상수를 선언하는 데 사용됨
- 선언 단계만 호이스팅되기 때문에, reference error 발생
- 객체나 배열과 같은 참조형 데이터의 경우, 해당 값의 내부 내용은 변경될 수 있음
