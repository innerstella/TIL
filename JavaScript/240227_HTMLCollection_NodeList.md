- DOM API가 여러 개의 결과값을 반환하기 위한 DOM 컬렉션 객체
- 유사 배열 객체이면서 이터러벌
  - for…of 순회 가능
  - 스프레드 문법을 통해 배열 변환 가능
- HTMLCollection : 언제나 live 객체
- NodeList : 대부분의 경우 노드 객체의 상태 변화를 실시간으로 반영하지 않고 과거의 정적 상태를 유지는 non-live 객체로 동작하지만, 경우에 따라 live 객체로 동작할 때가 있다

### HTMLCollection (live 객체)

- getElementByTagName, getElementsByClassName이 반환하는 객체
- 살아있는 DOM 컬렉션 객체
- 실시간으로 노드 객체의 상태 변경을 반영하여 요소를 제거할 수 있기 때문에 HTMLCollection 객체를 for 문으로 순회하면서 노드 객체의 상태를 변경할 때 주의해야 한다 (그러니까 red가 3개인데 앞에서부터 blue로 변경하면 실시간으로 red는 2개로 줄어서 그다음 2번째가 건너뛰고 바뀔 수 잇다. 그니까 순서가 꼬일 수 있다는 것임)
  - for 문을 역방향으로 순회하는 방법으로 회피 가능
  - while문으로 HTMLCollection 객체에 노드 객체가 남아 있지 않을 때까지 무한 반복하는 방법으로도 회피 가능
  - 더 간단한 해결책은 부작용 발생 원인인 HTMLCollection 객체를 사용하지 않는 것
    - 배열로 변환하면 forEach, map, filter, reduce 등을 사용할 수 있다

### NodeList (non-live 객체)

- HTMLCollection 객체의 부작용 해결
- querySelectorAll 사용
  - DOM 컬렉션 객체인 NodeList 객체 반환
- non-live 객체
  - 실시간으로 노드 객체의 상태 변경 반영 안함 (과거의 정적 상태 유지)
  - forEach 메서드 사용 가능
- childNodes 프로퍼티가 반환하는 NodeList 객체는 HTMLCollection 객체와 같이 실시간으로 노드 객체의 상태 변경을 반영하는 live 객체로 동작하므로 주의가 필요함

<aside>
💡 HTMLCollection이나 NodeList 객체는 예상과 다르게 동작할 때가 있어 다루기 까다롭고 실수하기 쉽다.

따라서 노드 객체의 상태 변경과 상관없이 안전하게 DOM 컬렉션을 사용하려면 **`HTMLCollection이나 NodeList 객체를 배열로 변환하여 사용하는 것`**을 권장한다. (모두 유사배열객체이기 때문에 스프레드로 간단하게 변환 가능)

</aside>
