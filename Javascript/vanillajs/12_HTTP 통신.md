# HTTP 통신

## 1. HTTP/HTTPS🌟

### 1) HTTP

- **프로토콜**: 미리 약속된 규칙
  - HTTP 요청: **클라이언트**가 서버에게 요청하는 것
    - 요청 **헤더**: 서버로 요청할 때 보내는 헤더
      - 사이트 주소뿐만 아니라 사용중인 시스템 정보와 웹 브라우저 정보, 사용한 언어 등 다른 정보
  - HTTP 응답: **서버**가 클라이언트에게 응답하는 것
    - 응답 **헤더**: 서버가 응답할 때 보내는 헤더
      - 응답 메시지를 보내는 시간, 메시지를 클라이언트에 어떻게 표시할지 등의 정보
    - 응답 **본문**: 이미지나 텍스트 같은 실제 사이트 내용

### 2) 요청 메소드(GET, POST)

- `GET`
  - 웹 브라우저의 주소 표시줄에 **요청 메시지가 함께 표시**되고 따로 요청 본문은 사용하지 않는다.
  - 요청 자료가 무엇인지 공개되더라도 문제가 없을 경우 사용하는 방식
- `POST`
  - **요청 내용이 겉으로 드러나지 않고** `요청 본문(request body)`에 따로 담아서 보낸다.
  - 요청 자료가 무엇인지 공개되면 안되는 경우 사용하는 방식

### 3) 응답 상태

- 클라이언트의 요청을 받은 서버가 필요한 작업을 처리하고 그 결과를 클라이언트로 보낼 때 응답 상태를 ‘상태’ 칼럼에 **숫자**로 표시

- `2XX`: 자료 요청을 수락했거나 자료 전송이 성공적으로 끝남.
  |상태|메세지|기능|
  |:--:|:--:|:--:|
  |200|OK|요청 성공|
  |202|Accepted|요청 성공, 요청 처리 중|

- `4XX`: 클라이언트에서 주소를 잘못 입력했거나 요청이 잘못됨.
  | 상태 | 메세지 | 기능 |
  | :--: | :-------------: | :--------------------------------: |
  | 400 | Bad Request | 요청 실패, 요청 메시지에 문법 오류 |
  | 401 | Unauthorized | 요청 실패, 인증 실패 |
  | 403 | Forbidden | 요청 실패, 서버가 요청 거부 |
  | 404 | Not Found | 요청 실패, 요청한 리소스 없음 |
  | 408 | Request Timeout | 요청 실패, 요청 시간 초과 |

- `5XX`: 서버 측의 오류로 요청을 처리할 수 없음.
  | 상태 | 메세지 | 기능 |
  | :--: | :-------------------: | :------------------------------: |
  | 500 | Internal Server Error | 요청 실패, 서버 내부 오류 |
  | 503 | Service Unavailable | 요청 실패, 서버가 요청 처리 불가 |

## 2. JSON🌟

### 1) 데이터 교환 방식

- 대표적으로 XML, JSON이 있다. 최근에는 JSON이 XML을 대체하고 있다.

### 2) JSON 특징

- **텍스트**로만 구성되었기 때문에 서버와 클라이언트 사이에 주고 받을 때 전송 속도가 아주 **빠르다**.
- JSON은 **프로그래밍 언어나 플랫폼에 대해 독립적**이기 때문에 C++이나 자바, 자바스크립트, 파이썬 등 많은 언어에서 사용할 수 있다.
- 자바스크립트 사용자라면 **누구나 알고 있는 표기법**을 사용하기 때문에 읽기도 쉽고 필요에 따라 **자바스크립트 객체로 변환**하기도 쉽다.

### 3) JSON 형식

- 중괄호{} 사이에 `이름`과 `값`으로 구성된다.

  ```json
  {
    "이름": "값"
  }
  ```

- JSON '**이름**'

  - 반드시 **큰 따옴표("")로** 묶어야 한다.
  - 공백이나 하이픈(-), 언더바(\_)를 함께 사용할 수 있다.
    - 공백이나 하이픈이 있을 경우 프로그램을 통해 그 이름에 접근할 때 쉽지 않기 때문에 둘 이상의 단어로 된 이름을 사용한다면 **언더스코어(\_)를** 사용하는 것이 좋다.

- JSON '**값**'

  - **숫자형**: 정수와 실수 모두 사용(8진수나 16진수를 사용한 표기법 제외)
  - **단순 문자열**: 항상 큰 따옴표("")로 묶어야 한다.
  - **논릿값과 null**
  - **JSON 문자열, 배열**
    - JSON 문자열 안에 또 다른 JSON 문자열을 넣을 수도 있다.
    - 배열 사용시에는 일반 배열과 마찬가지로 대괄호([ ])를 사용

  ```json
  {
    "이름": "홍길동",
    "나이": 25,
    "성별": true,
    "주소": null,
    "특기": ["농구", "도술"],
    "가족관계": {
      "아버지": "홍판서",
      "어머니": "춘섬",
      "형": "홍충일",
      "나": "홍길동"
    }
  }
  ```

  - 여러 개의 JSON 문자열을 하나의 배열 형태로 저장할 수도 있다.

    ```json
    [
      {
        "name": "최유리"
      },
      {
        "name": "김철수"
      }
    ]
    ```

### 6) 객체와 JSON 형식 변환

```js
// JSON.stringify(): 객체를 JSON 형식으로 변환

let me1 = { name: "김철수", age: 25, address: "서울시" };
let jsonText1 = JSON.stringify(me); //직렬화(stringify)

// JSON.parse(): JSON 형식을 객체로 변환
let jsonText2 = '{"name":"김철수","age":25,"address":"서울시"}';
let me2 = JSON.parse(jsonText); //파싱(parsing)
```

## 3. 서버에서 자료 가져오기🌟

### 1) 일반적인 서버와 클라이언트의 통신

- 웹 브라우저에서 url 주소를 입력하여 서버 컴퓨터로 접속
- 서버 컴퓨터는 클라이언트 컴퓨터에게 요청한 자료를 전송
- 클라이언트 컴퓨터는 서버 컴퓨터로부터 받은 자료를 웹 브라우저에 표시

### 2) 비동기적 통신

- 화면을 스크롤하면 사이트 전체가 새로 고쳐지는 것이 아니라 스크롤 영역만 새로 고쳐지는 것을 볼 수 있다.
- `AJAX(Asynchronous JavaScript And XML)`는 이런 비동기적 통신을 지원하는 자바스크립트의 라이브러리이다.

### 3) XMLHttpRequest 객체

- `XML`이라는 자료를 `HTTP` 프로토콜을 사용해서 `Request(요청)`한다.
- `XMLHttpRequest` 객체는 **서버와 통신(HTTP)할 때 사용**하는 자바스크립트의 객체이다.

  - 프로퍼티와 메서드를 사용해서 자료를 주고 받거나 상태를 체크
  - 웹 페이지 전체가 아니라 **필요한 부분의 자료만** 가져올 수 있다.

### 4) XMLHttpRequest 이용하기

- XMLHttpRequest 객체 만들기
  - new 예약어를 사용해서 XMLHttpRequest 객체의 인스턴스를 만든다.
  ```js
  let xhr = new XMLHttpRequest();
  ```
- `open(방식, 자료위치, 비동기여부)`

  - 어떤 자료를 가져올지 지정
  - 방식: GET, POST
  - 자료위치: 서버의 파일 경로
  - 비동기여부: true(비동기, 기본), false(동기)

- `send(내용)`

  - 서버로 요청 전송
    - GET 방식: send() 메서드에 아무것도 넣지 않거나 null을 넣는다.
    - POST 방식: send() 메서드에 서버로 전송할 내용을 넣는다.

  ```js
  // GET
  xhr.open("GET", "http://localhost:8080/json");
  xhr.send();

  // POST
  xhr.open("POST", "http://localhost:8080/json");
  xhr.send("name=홍길동&age=25");
  ```

- `readyState` 프로퍼티
  - XMLHttpRequest 객체의 **현재 상태**를 나타낸다.
  - 아래 상태를 0부터 4까지 순서대로 거쳐가면서 통신이 이루어진다.
    | 값 | 의미 |
    |:---:|:---:|
    | 0 | 아무 요청도 하지 않은 상태 |
    | 1 | 서버로 자료를 **요청**하고 성공한 상태|
    | 2 | 서버 요청에 대한 응답으로 **헤더**가 도착한 상태 |
    | 3 | 서버에서 자료들이 로딩 중인 상태 |
    | 4 | 모든 데이터를 받은 상태 |
- `status`, `statusText` 프로퍼티
  > 위 HTTP 통신에서 HTTP 응답 상태, 메세지 표를 참고하자!
  - `status`: 서버의 HTTP **상태 코드**
  - `statusText`: 서버의 응답 **설명** 메시지
- `readyState`와 `status` 사용

  - readyState 값이 바뀔 때마다 `readystatechange 이벤트`가 발생
  - `readystatechange 이벤트`가 발생할 때마다 `readyState`와 `status` 프로퍼티를 사용해서 서버와 통신 상태를 체크한다.

    - readyState 값은 요청이 성공했는지만을 알려주기 때문에 **만약 서버에 없는 파일을 요청하더라도 readyState 값은 4이다.**
    - 요청에 성공하고 서버에서 필요한 파일을 가져왔는지 체크하려면 **status 값**을 확인해야 한다.

    ```js
    xhr.onreadystatechange = function () {
      if (xhr.readyState === 4 && xhr.status === 200) {
        // 서버에서 자료를 정상적으로 가져왔을 때 실행할 코드
      }
    };
    ```

- `response`, `responseText` 프로퍼티

  - `response`: 요청에 대한 응답
  - `responseText`: 서버에서 받은 자료를 **문자열**로 저장
  - `responseType`: 응답 **데이터의 종류**를 지정
  - `responseURL`: 응답을 보낸 URL
  - `responseXML`: HTML이나 XML 같은 형식의 데이터를 받아올 때 사용

- 사용 예시

  ```js
  let xhr = new XMLHttpRequest();
  xhr.open("GET", "http://localhost:8080/json"); // json 파일을 요청
  xhr.send();

  xhr.onreadystatechange = function () {
    if (xhr.readyState === 4 && xhr.status === 200) {
      let result = JSON.parse(xhr.responseText);
    }
  };
  ```

## 4. 예외 처리 하기
