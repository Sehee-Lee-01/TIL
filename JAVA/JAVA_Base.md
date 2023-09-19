# JAVA의 기본

## JDK, JRE, JVM

- 우선 요약하자면, JDK는 JRE를 포함하고 있고, JRE는 JVM을 포함하고 있다.

### JVM(Java Virtual Machine)

- 자바를 돌리는 프로그램
- JVM의 특징
  - OS에 종속적이지 않다. 어느 기기 위에서든 실행 가능하다.(**WORA**)
  - 가비지 컬렉터(Garbage Collector)를 통해 메모리를 관리한다.
    - 가비지 컬렉터: 메모리를 관리하는 프로세스

### JRE(Java Runtime Environment)

- JVM과 라이브러리 등을 포함하고 있다.
- 프로그램 **실행환경** 구성 (`java`)

### JDK(Java Development Kit)

- JRE와 개발에 필요한 도구를 포함하고 있다.
- 프로그램 **개발환경** 구성(`java`, `javac`)
- 종류
  - OpenJDK
  - Oracle JDK

## 자동으로 빌드하고 실행해주는 Build Tool: Gradle

- `java`와 `javac`를 사용해서 컴파일하고 실행하는 것은 번거롭다. 이를 더욱 더 쉽게 해주는 툴이라고 보면 된다. (약간 npm, yarn 같은 느낌)
- Gradle은 Groovy라는 언어를 사용한다.
- Gradle은 `build.gradle` 파일을 통해 설정한다.
  - 어떤 방식으로 빌드할 것인지
- 명령어
  - `gradle init`: 프로젝트 초기화
  - `gradle build`: 빌드
  - `gradle run`: 실행
  - 그 외 명령어는 gradle tasks를 통해 확인 가능하다.

## JAVA 코딩 컨벤션

- 클래스명은 앞글자가 대문자인 카멜케이스
- 메소드나 변수명은 앞글자가 소문자인 카멜케이스
- 상수는 모두 대문자
- indent는 tab or space로 작성하되, 섞어서 쓰면 안된다.

## 래퍼런스

- C/C++ 처럼 alloc/free를 하지 않는다.
- 포인터 대신 래퍼런스라는 개념이 있다.
  - primitive type을 제외한 모든 타입은 **래퍼런스 타입**이다.

## Constant Pool

- String은 Constant Pool이라는 곳에 저장된다.
  - Constant Pool: 런타임에 생성되는 상수 저장소
  - GC(가비지 컬렉터)의 대상이 아니다.
- StringBuilder와 StringBuffer
  - 공통점: 클래스 내부적으로 버퍼를 가지고 있어 문자열 연산이 String보다 빠르다.(공간의 낭비도 없다.)
  - StringBuilder: 동기화를 지원하지 않는다. Thread-safe하지 않다.
  - StringBuffer: 동기화를 지원한다.
    - **동기화**: 멀티 스레드 환경에서 현재 데이터를 사용하고 있는 스레드가 끝날 때까지 다른 스레드가 접근하지 못하도록 막는 것
    - 비동기로 동작하는 경우가 많을 때는 StringBuffer를 사용하는 것이 좋다.

## Object

- 모든 클래스의 최상위 클래스이다.
  - 모든 클래스는 Object 메소드를 사용할 수 있다.
- 대표 메소드
  - `toString()`: 객체의 정보를 문자열로 반환한다.
  - `equals()`: 객체의 내용이 같은지 비교한다.
  - `hashCode()`: 객체의 해시코드를 반환한다.

## 참고

- [[Java] JDK? JRE? JVM?](https://m.blog.naver.com/goreng2/221770110714)
- [자바의 String과 Constant Pool](https://jiwondev.tistory.com/114)
- [☕ JDK / JRE / JVM 개념 & 구성 원리 💯 총정리](https://inpa.tistory.com/entry/JAVA-%E2%98%95-JDK-JRE-JVM-%EA%B0%9C%EB%85%90-%EA%B5%AC%EC%84%B1-%EC%9B%90%EB%A6%AC-%F0%9F%92%AF-%EC%99%84%EB%B2%BD-%EC%B4%9D%EC%A0%95%EB%A6%AC)
- [☕ 자바 String / StringBuffer / StringBuilder 차이점 & 성능 비교](https://inpa.tistory.com/entry/JAVA-%E2%98%95-String-StringBuffer-StringBuilder-%EC%B0%A8%EC%9D%B4%EC%A0%90-%EC%84%B1%EB%8A%A5-%EB%B9%84%EA%B5%90#:~:text=%EB%91%90%20%ED%81%B4%EB%9E%98%EC%8A%A4%EB%8A%94%20%EB%AC%B8%EB%B2%95%EC%9D%B4%EB%82%98,%EC%95%88%EC%A0%84%ED%95%98%EA%B2%8C%20%EB%8F%99%EC%9E%91%ED%95%A0%20%EC%88%98%20%EC%9E%88%EB%8B%A4.)
