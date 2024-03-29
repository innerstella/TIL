## HTTP 메서드

- 클라이언트와 서버 사이에 이루어지는 요청과 응답 데이터를 전송하는 방식
- 주요 메소드 : GET, POST, PUT, PATCH, DELETE
- 기타 메소드 : HEAD, OPTIONS, CONNECT, TRACE

### `GET`

- 리소스 조회
- URL 형식으로 서버 측에 리소스를 요청함
  - 쿼리 스트링 외 메시지 바디를 사용해서 데이터를 전달할 수 있지만, 서버에서 따로 구성해야 되기 때문에 지원하지 않는 곳이 많아서 권장하지 않음
- 조회 시 `POST` 도 사용 가능하지만, `GET` 메서드는 캐싱이 가능해서 유리함
- 정적 데이터 조회 과정
  - 용도 : 이미지, 정적 텍스트 문서 조회 등
  - 방법 : 쿼리 파라미터 없이, 리소스 경로로 단순하게 조회 가능
- 동적 데이터 조회 과정
  - 용도 : 검색어 등
  - 방법 : 요청 url 뒤에 쿼리 파라미터로 데이터 전달 `key1=value1&key2=value2`
  -

### `POST`

- 전달한 데이터 처리/생성 요청
- 메시지 바디를 통해 서버로 요청 데이터를 전달하면, 서버는 요청 데이터를 처리하여 업데이트
- 데이터 조회 시, JSON으로 조회 데이터를 넘겨야 하는 경우에는 `POST` 를 사용하기도 함

### `PUT`

- 리소스를 갱신하기 위함
- 해당 리소스가 없으면 생성

### `PATCH`

- 리소스의 일부분만 갱신하기 위함
  | POST             | PUT                   | PATCH                       |
  | ---------------- | --------------------- | --------------------------- |
  | 리소스 신규 등록 | 기존 리소스 전체 변경 | 기존 리소스의 일부분만 변경 |

### `DELETE`

- 리소스를 삭제하기 위함
- 웹 서버 측에 요청한 리소스를 삭제할 때 사용함

### `HEAD`

- 메시지 헤더 정보를 받기 위함 → 서버의 응답 헤더를 봄으로써 리소스가 수정되었는 지 확인 가능
- 서버에서 body를 리턴하지 않음
  | GET                       | HEAD                                        |
  | ------------------------- | ------------------------------------------- |
  | 실제 문서 요청            | 실제 문서 요청이 아닌 문서에 대한 정보 요청 |
  | body에 데이터가 담겨 있음 | body는 비어 있고, header 정보만 들어 있음   |

### `OPTIONS`

- 예비 요청 (Preflight)에 사용됨
  - 예비 요청 : 본 요청을 하기 전에 안전한지 미리 검사하는 것
- 서버 측 제공 메소드에 대한 질의를 하기 위함
- 웹 서버 측에서 지언하고 있는 메소드가 무엇인지 알기 위해 사용
- 서버의 지원 가능한 HTTP 메서드와 출처를 응답 받아 CORS 정책을 검사하기 위한 요청

### `CONNECT`

- 클라이언트와 서버 사이의 중간 경유를 위함
- 보통 Proxy를 통해 SSL 통신을 하고자 할 때 사용함

### `TRACE`

- 리퀘스트 리소스가 수신되는 경로를 보기 위함
- 웹 서버로부터 받은 내용을 확인하기 위해 loop-back 테스트를 할 때 사용함

---

### 참고 자료

1. [https://gyoogle.dev/blog/web-knowledge/HTTP Request Methods.html](https://gyoogle.dev/blog/web-knowledge/HTTP%20Request%20Methods.html)
2. [https://inpa.tistory.com/entry/WEB-🌐-HTTP-메서드-종류-통신-과정-💯-총정리](https://inpa.tistory.com/entry/WEB-%F0%9F%8C%90-HTTP-%EB%A9%94%EC%84%9C%EB%93%9C-%EC%A2%85%EB%A5%98-%ED%86%B5%EC%8B%A0-%EA%B3%BC%EC%A0%95-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC)
