# [프로그래머스 자바 입문 학습 기록](https://school.programmers.co.kr/learn/courses/5/5-%EB%AC%B4%EB%A3%8C-%EC%9E%90%EB%B0%94-%EC%9E%85%EB%AC%B8)

기존에는 코딩테스트를 위한 JAVA를 공부했지만 공부를 하면서 자료구조 설정, JAVA의 기본 기능에 대한 지식의 부족함을 많이 느꼈다. JAVA를 쓰고는 있지만 50%만 알고 있는 느낌이 들어 이번 기회에 JAVA를 더 제대로 쓸 수있도록 공부하고자 한다.

- 왜 개발 시에 버전이 중요할까? 왜 개발 시에 버전을 명시해야 할까?
- 추상클래스와 인터페이스의 차이점은 무엇일까? 왜 둘 다 필요한 것일까?
- 왜 int만 알면되지 Integer를 알아야 할까?
- 왜 String만 알면되지 StringBuffer, StringBuilder를 알아야 할까?

등에 대해서 반성하고 복습해본다,,,

## 타입

### 2차원 배열

- 2차원 배열에서 가변 크기의 배열을 만들 수 있다.

```java
int[][] arr = new int[3][];
arr[0] = new int[1];
arr[1] = new int[2];
arr[2] = new int[3];

int[][] arr2  = new int[][]{{1}, {1,2}, {1,2,3}};
```

### 참조타입

- 기본형 자료형을 제외한 모든 자료형은 참조타입이다. 즉, 참조타입은 값 자체가 아닌 **객체의 주소**를 저장하는 타입이다.
  - ex) 참조형 대표 예시인 String은 문자열을 저장하는 것이 아니라 문자열이 저장된 주소를 저장한다.(배열도 포함.)

## 클래스

#### String

- String은 문자열을 저장하는 것이 아니라 문자열이 저장된 주소를 저장한다.
- String은 **불변객체**이다. 즉, 한번 생성된 String은 변하지 않는다.

  - 문자열을 자주 변경해야 하는 경우에는 `StringBuffer`, `StringBuilder`를 사용한다.
  - `substring()` 메소드를 사용하면 새로운 String 객체를 생성한다. String 내용 자체는 변하지 않는다.

- String은 문자열을 저장하는 것이 아니라 문자열이 저장된 주소를 저장한다.

  - 두 문자열을 비교할 때는 `==`가 아닌 `equals()`를 사용한다.
  - `==`를 사용하면 두 문자열의 주소를 비교하기 때문에 문자열을 비교할 수 없다.

    ```java
    // str과 str2는 같은 주소를 가리킨다.
    // new 연산자를 사용하지 않으면 인스턴스는 무조건 새로 생성되지 않는다.
    String str = "abc"; // "abc" 메모리 중에서 '상수(불변)'가 저장되는 영역에 저장
    String str2 = "abc"; // "abc"가 이미 상수가 저장되어 있기 때문에 str과 같은 주소를 가리킨다.

    // str3은 str과 다른 주소를 가리킨다.
    // new 연산자를 사용하면 인스턴스는 무조건 새로 생성된다.
    String str3 = new String("abc"); // new 연산자를 사용하면 새로운 주소를 가리킨다.
    ```

- String 메소드
  - `concat()`: 문자열을 더한다.
    - `concat(String str)`: 문자열 str을 더한다.
    - 새로운 String 객체를 생성한다. 원래 클래스는 **변하지 않는다**.
  - `indexOf()`: 문자열의 위치를 반환한다.
    - `indexOf(String str)`: 문자열 str이 처음으로 등장하는 위치를 반환한다.
  - `substring()`: 문자열을 자른다.
    - `substring(int beginIndex, int endIndex)`: beginIndex부터 endIndex-1까지 문자열을 자른다.

### enum

- enum은 열거타입을 이용하여 변수를 선언할 때 변수타입으로 사용할 수 있다.
- 왜 사용 해야하는가?

  - 코드가 단순해지며, 가독성이 좋아진다.
  - 사용하지 않은 경우 발생 하는 문제점
    - enum 사용 이전에는 상수를 열거형 대신 사용했다.
    - 하지만 이렇게 사용할 경우 아래처럼 다른 값이 들어가게 되므로 문제를 발생시킬 수 있다.

  ```java
  public class Example {
    public static final String MALE = "MALE";
    public static final String FEMALE = "FEMALE";

    public static void main(String[] args) {
        String gender1;
        gender1 = Example.MALE;
        gender1 = "NON";
    }
  }
  ```

  - enum을 사용하면 이러한 문제를 해결할 수 있다.
    - **특정 값만 가져야 하는 경우에는 enum을 사용하는 것이 좋다.**

  ```java
  enum Gender {
      MALE, FEMALE;
  }
  Gender gender2;
  gender2 = Gender.MALE;
  gender2 = Gender.FEMALE;
  //  gender2 = "NON"; // 컴파일 에러 발생
  ```

### this

- 왜 `this.~`를 사용해야하는가?

  - this를 사용하지 않으면 아래와 같은 문제가 발생할 수 있다.
    - 아래 코드에서 this를 사용하지 않으면 가깝게 선언된 변수를 우선 사용하기 때문에 name과 age에 값을 할당할 수 없다.

  ```java
    public class Example {
        public String name;
        public int age;

        public Example(String name, int age) {
            name = name;
            age = age;
        }
    }
  ```

  - this를 사용하면 아래와 같이 가깝게 선언된 변수가 아닌 클래스의 변수를 사용할 수 있다.

  ```java
    public class Example {
        public String name;
        public int age;

        public Example(String name, int age) {
            this.name = name;
            this.age = age;
        }
    }
  ```

  - **코드가 단순할 때는 변수 이름, 메서드 이름을 정확히 구분할 수 있도록 명명하면 되지만 코드가 복잡해지면 비슷한 이름을 가진 변수나 메서드가 많이 생긴다. 이럴 때 this를 사용하면 클래스의 변수나 메서드임을 명확히 할 수 있다.**

- `this()`

  - this()는 생성자에서 다른 생성자를 호출할 때 사용한다.

  ```java
    public class Example {
        public String name;
        public int age;

        public Example() {
            this("이름없음", 1); // 코드 중복을 막을 수 있다.
        }

        public Example(String name, int age) {
            this.name = name;
            this.age = age;
        }
    }
  ```

### 오버로딩

- 오버로딩은 같은 이름의 메서드를 여러 개 가지면서 **매개변수의 유형과 개수**가 다르도록 하는 기술이다.
- 장점
  - 매개변수가 다르더라도 비슷한 기능을 하는 메서드의 경우 메서드의 이름을 짓는 고민을 덜 수 있다.
  - 가독성이 좋아진다.

### 오버라이딩

- 오버라이딩은 상위 클래스가 가지고 있는 메서드를 **하위 클래스가 재정의**하여 사용하는 기술이다.
- 장점
  - 상위 클래스의 메서드를 재정의하여 사용할 수 있다.

### 접근 제한자

- 접근 제어자는 클래스, 변수, 메서드의 사용을 제한할 수 있다.
- 접근 제어자의 종류
  - public: 모든 접근을 허용한다.
  - protected: 같은 패키지 내에서, 그리고 다른 패키지의 자손 클래스에서 접근이 가능하다.
  - default: 같은 패키지 내에서만 접근이 가능하다. **다른 패키지의 자손 클래스에서 접근이 불가능하다.**
    - 접근 제어자를 **명시하지 않으면** default 접근 제어자가 적용된다.
  - private: 같은 클래스 내에서만 접근이 가능하다.

### 인터페이스

- 인터페이스의 특징

  - 인터페이스는 **추상 메서드**와 **상수**만을 멤버로 가질 수 있는 클래스이다.
  - 인터페이스는 클래스와 달리 **다중 상속**이 가능하다.
  - 인터페이스는 인스턴스를 생성할 수 없다.
  - 인터페이스의 추상 메서드는 public abstract가 생략되어 있다.
  - 인터페이스의 상수는 public static final이 생략되어 있다.
  - 인터페이스가 가지고 있는 메소드를 하나라도 구현하지 않는다면 해당 클래스는 추상클래스가 된다.

### 내부 클래스

- 클래스 안에 선언된 클래스

1. 중첩클래스

- 인스턴스 클래스: 클래스 안 필드를 선언하는 위치에 선언
- 스태틱 클래스: 클래스 안 필드를 선언하는 위치에 static으로 선언

2. 지역클래스

- 메서드 안에 선언된 클래스

  ```java

  class Outer {
      class InstanceInner {
          int iv = 100;
      }

      static class StaticInner {
          int iv = 200;
          static int cv = 300;
      }

      public void myMethod() {
          // 메소드 내에서 이용 가능
          class LocalInner {
              int iv = 400;
          }

          LocalInner localInner = new LocalInner();
          System.out.println(localInner.iv);
      }

      public void main(String[] args) {
          Outer outer = new Outer();
          InstanceInner instanceInner = outer.new InstanceInner();
          System.out.println(instanceInner.iv);

          StaticInner staticInner = new StaticInner();
          System.out.println(staticInner.iv);
          System.out.println(StaticInner.cv);
      }
  }
  ```

3. 익명(중첩)클래스

- 클래스의 선언과 객체의 생성을 동시에 하는 이름없는 클래스
- 익명클래스를 만드는 이유는 특정 클래스를 상속받는 클래스를 만들 필요가 없을 경우
- **해당 클래스에서만 사용되고 다른 클래스에서는 사용되지 않는 경우**

  ```java
  public abstract class Action{
          public abstract void exec();
  }

  public class ActionExam{
      public static void main(String args[]){
          Action action = new Action(){
              public void exec(){
                  System.out.println("exec");
              }
          };
          action.exec();
      }
  }

  ```

## 예외

### 예외처리

- Exception 클래스

  - 모든 예외의 최고 조상 클래스
  - 예외 처리 시 모든 예외를 처리할 수 있다.

- Throws

  - 예외가 발생했을때 예외를 호출한 쪽에서 처리하도록 던져준다.

- Throw

  - 예외를 강제로 발생시킨다.(익셉션이 발생)
  - **왜 예외를 발생 시켜야 할까?**
    - **리턴 값으로 예외를 처리할 수 없는 경우에는 예외를 발생시켜야 한다.**

  ```java
  // 예외를 발생시켜야 하는 경우
  public static int divide(int i, int j) throws IllegalArgumentException{
    if(j == 0){
        System.out.println("2번째 매개변수는 0이면 안됩니다.");
        return 0; // retrun 값이 잘못 retrun된다.
        throw new IllegalArgumentException("0으로 나눌 수 없어요."); // 예외를 발생시킨다.
    }
    int k = i / j;
    return k;
  }

  ```

- 사용자 정의 Exception
  - Exception 클래스를 상속받아 사용자 정의 Exception을 만들 수 있다.
  - Checked Exception: Exception 클래스를 상속
    - 반드시 오류를 처리 해야만 하는 Exception
      - 예외 처리하지 않으면 컴파일 오류를 발생 시킨다.
  - Unchecked Exception: RuntimeException 클래스를 상속
    - 예외 처리하지 않아도 컴파일 시에는 오류를 발생시키지 않는다.
  - **왜 새로 만드는가?**
    - 기존의 Exception 클래스를 사용하면 어떤 예외가 발생했는지 알 수 없다.
    - **이름 만으로 어떤 예외가 발생했는지 알 수 있도록 사용자 정의 Exception을 만들 수 있다.**
  ```java
  public class BizException extends RuntimeException{
    // 해당 생성자를 생성할 때는 부모 생성자에게 전달하면 된다.
      public BizException(String msg){ // 문자열로 된 오류메세지를 담는 생성자
          super(msg);
      }
      public BizException(Exception ex){ // 실제 발생할 익셉션을 담는 생성자
          super(ex); // 부모의 생성자에게 ex를 넘김
      }
  }
  ```
