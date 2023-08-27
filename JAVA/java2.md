# [프로그래머스 자바 중급](https://school.programmers.co.kr/learn/courses/9/9-%EC%9E%90%EB%B0%94-%EC%A4%91%EA%B8%89)

중급에서는 클래스, 자료구조, IO등에 대해서 더 자세히 알아본다.
기존에 사용했지만 잘 이해하지 못했던 각종 패키지에 대해서도 알아본다.

## 최상위 클래스 Object

### Object 클래스

- 모든 클래스의 **최상위 클래스**
- 모든 클래스는 Object 클래스를 상속받는다.
  - **Object 클래스의 메소드를 사용할 수 있다.**
- 대표 메소드
  - `toString()`: 객체의 정보를 문자열로 제공한다.
  - `equals()`: 객체의 정보가 같은지 비교한다.
    - 기본형 자료형은 값을 비교하지만 참조형 자료형은 **주소**를 비교한다.
    - 정보를 비교하고 싶다면 equals()를 오버라이딩 해야한다.
  - `hashCode()`: 객체의 해시코드 값을 반환한다.

## java.lang 패키지(기본 제공)

- 자바에서 기본적으로 제공하는 패키지
  - import 없이 사용할 수 있다.
- 대표 클래스
  - Object
  - System
  - Class
  - String
  - StringBuffer, StringBuilder
  - Math
  - Wrapper 클래스
  - Enum

### Wrapper 클래스

- **왜 사용하는가?**
  - **형변환과 비교연산을 하기 위해서**
- 오토박싱: 기본형 자료형을 참조형으로 자동 변환해주는 기능
- 언박싱: 참조형 자료형을 기본형으로 자동 변환해주는 기능

  ```java
  Integer i = 10; // 오토박싱(java5부터 지원한다.)
  int j = i; // 언박싱(java5부터 지원한다.)
  ```

### StringBuiler, StringBuffer

- String은 불변객체이다. 즉, 한번 생성된 String은 변하지 않는다.
- 이러한 String의 단점을 보완하기 위해 나온 것이 StringBuffer, StringBuilder이다.

## java.util 패키지

- 대표 클래스
  - Date
  - Calendar
  - Random
  - Scanner
  - StringTokenizer
  - ArrayList
  - LinkedList
  - HashMap
  - HashSet
  - Arrays
  - Collections

### 컬렉션 프레임워크

- Collection 인터페이스
  - 자료구조를 다루는 클래스이다.
  - Collection은 **인터페이스**이다. 즉, 인스턴스를 생성할 수 없다.
  - 컬렉션에서 가장 기본이 되는 인터페이스이다.
  - 중복을 허용하고 저장된 순서도 기억하고 있지 않다.
  - 대표 메서드
    - `add()`: 객체를 추가한다.
    - `size()`: 객체의 개수를 반환한다.
    - `iterator()`: 객체를 순회한다.
    - `remove()`: 객체를 삭제한다.
      - `hasNext()`: 다음 객체가 있는지 확인한다.
      - `next()`: 다음 객체를 반환한다.
- Collection을 상속하는 자료구조
- List 인터페이스: 순서가 있는 데이터의 집합, 중복을 허용한다.
  - `get()`: 순서를 기억하고 있기 때문에 인덱스를 통해 객체를 가져올 수 있다.
  - 대표적인 클래스
    - ArrayList
    - LinkedList
- Set 인터페이스: 중복을 허용하지 않는 인터페이스
  - `add()`: 같은 자료가 있으면 false 반환, 아니면 true 반환
  - 대표적인 클래스
    - HashSet
    - TreeSet
- Map 인터페이스: 키와 값으로 이루어진 데이터를 저장하는 인터페이스
  - `put()`: 키와 값을 저장한다.
  - `get()`: 키를 통해 값을 가져온다.
  - `keySet()`: 키(중복 X)를 Set으로 반환한다.
  - 대표적인 클래스
    - HashMap
    - TreeMap

### Generic

- 인스턴스를 만들때 사용하는 타입을 지정하는 문법이다.(java5부터 지원)
- **왜 사용하는가?**

  - **인스턴스를 만들 때 사용하는 타입을 지정**
  - **사용시에는 구체적인 타입을 설정함으로써 다양한 타입의 클래스를 이용하는 클래스를 만들 수 있다.**

  ```java
  // 가상의 클래스 T를 사용한다.
  public class Box<T> {
      private T t;
      public T get() {
          return t;
      }
      public void set(T t) {
          this.t = t;
      }
  }
  ```

### List

- Collection 인터페이스를 상속받는 인터페이스이다.
- 특징
  - 중복을 허용한다.
  - 저장된 순서를 기억한다.
- 대표적인 클래스
  - ArrayList: 배열로 구현되어 있다.
  - LinkedList: 리스트로 구현되어 있다.

### Set

- Collection 인터페이스를 상속받는 인터페이스이다.
- 특징
  - 중복을 허용하지 않는다.
  - 저장된 순서를 기억하지 않는다.
- 대표적인 클래스
  - HashSet: 순서를 기억하지 않는다.
  - TreeSet: 정렬된 순서로 저장한다.

### Map

- **Set** 인터페이스를 의존하는 인터페이스이다.
- 특징
  - 키와 값으로 이루어진 데이터를 저장한다.
  - 키는 중복을 허용하지 않는다.
  - 값은 중복을 허용한다.
- 대표적인 클래스
  - HashMap: 순서를 기억하지 않는다.
  - TreeMap: 정렬된 순서로 저장한다.

## 날짜와 시간

### _Date_ → **Calendar**

- Date 클래스

  - 날짜와 시간을 다루는 클래스이다.
  - Date 클래스의 생성자와 메소드는 대부분 **deprecated** 되었다. 즉, 사용을 권장하지 않는다.
  - **지역화 지원이 되지 않는다.**

    - 지역화: 지역에 따라서 시간, 통화(원, 달러, 엔 등) 언어등에 대하여 고려하는 프로그래밍을 지역화에 맞춘 프로그래밍

    ```java
    Date date = new Date();
    System.out.println(date.toString()); // Sat May 08 16:47:00 KST 2021

    // 원하는 형식으로 출력하기 위해서는 SimpleDateFormat 클래스를 사용한다.
    SimpleDateFormat ft = new SimpleDateFormat("yyyy.MM.dd 'at' hh:mm:ss a zzz");
    System.out.println(ft.format(date)); // 2021.05.08 at 04:47:00 PM KST

    // Long 타입의 시간으로 변환1: getTime() 메소드를 사용한다.
    long time = date.getTime();
    System.out.println(time); // 1620454020000

    // Long 타입의 시간으로 변환2: System.currentTimeMillis() 메소드를 사용한다.
    long time2 = System.currentTimeMillis();
    ```

- Calendar 클래스

  - Date 클래스의 단점을 보완하기 위해 나온 클래스이다.
  - Calendar 클래스는 추상 클래스이다. 즉, 인스턴스를 생성할 수 없다.

    - Calendar 클래스의 인스턴스를 생성하려면 Calendar 클래스의 **getInstance()** 메소드를 사용해야 한다.(팩토리 패턴)

      - getInstance()메소드를 호출하면 내부적으로 java.util.GregorianCalendar 인스턴스를 만들어서리턴한다.
      - GregorianCalendar는 Calendar의 자식 클래스이다.

    - **왜 추상 클래스로 만들었을까?**
      - **다양한 형태의 달력을 지원하기 위해서**
      - GregorianCalendar 달력이 다른 달력으로 바뀌어도, 사용자는 예전처럼 getInstance() 메소드를 통해 Calendar 클래스의 인스턴스를 생성할 수 있다.

  - Calendar 클래스는 **날짜와 시간을 계산하는 메소드**를 제공한다.

  ```java
  Calendar cal = Calendar.getInstance();

  // get(): Calendar 클래스를 이용해서 현재 날짜와 시간에 대한 정보를 얻는 방법
  //  Calendar의 상수를 사용하여 날짜와 시간에 대한 정보를 얻을 수 있다.
  System.out.println(cal.get(Calendar.YEAR)); // 2021
  System.out.println(cal.get(Calendar.MONTH) + 1); // 월은 0부터 시작하기 때문에 +1을 해줘야 한다.
  System.out.println(cal.get(Calendar.DATE)); // 8
  System.out.println(cal.get(Calendar.HOUR)); // 4
  System.out.println(cal.get(Calendar.MINUTE)); // 59
  System.out.println(cal.get(Calendar.SECOND)); // 0

  // add(): Calendar 클래스를 이용해서 날짜와 시간을 계산하는 방법
  cal.add(Calendar.HOUR, 5); // 5시간을 더한다.
  cal.add(Calendar.YEAR, -1); // 1년을 뺀다.
  ```

### java.time 패키지

- Java에서 제공하는 Date, Time API는 부족한 점이 많다.
  - JDK 코어에서 이런 문제를 해결하기 위해 새롭게 디자인하여 나온 API가 java.time 패키지이다.
- 특징
- factory method를 이용하여 인스턴스를 생성한다.

  - **factory method**: 인스턴스를 생성하는 메소드
  - 오브젝트 자기 자신의 특정 요소를 가지고 오브젝트를 생성할 경우 `of` 메서드를 호출하면 되고, 다른 타입으로 변경할 경우에는 `from` 메서드를 호출하면 된다.

  ```java
  // now(): 현재 날짜와 시간을 가져오는 방법
  LocalDateTime now = LocalDateTime.now();

  // of() : 특정 날짜와 시간을 가져오는 방법
  LocalDateTime of = LocalDateTime.of(2021, 5, 8, 17, 30, 0);
  LocalDate of2 = LocalDate.of(2021, Month.DECEMBER, 8); // Month는 enum이다.
  LocalTime of3 = LocalTime.of(17, 30, 0);

  // to*(): 다른 타입으로 변경하는 방법
  LocalDate toLocalDate = now.toLocalDate();
  LocalTime toLocalTime = now.toLocalTime();

  // get*(): 날짜와 시간에 대한 정보를 얻는 방법
  System.out.println(now.getYear()); // 2021
  System.out.println(now.getMonth()); // MAY
  ```

## IO

### IO란?

- Input과 Output의 약자이다.

  - 프로그램이 외부와 데이터를 주고 받는 것을 의미한다.
  - 열고 꼭 닫아야 한다.

- IO의 종류

  - **바이트 기반**과 **문자 기반**으로 나눌 수 있다.

    - Byte 기반 입출력 클래스

      - **Byte 단위**로 데이터를 전송한다.
      - 대표 추상 클래스
      - InputStream: 입력
      - OutputStream: 출력

    - 문자(Char) 입출력 클래스

      - **문자(Char) 단위**로 데이터를 전송한다.
      - 대표 추상 클래스
      - Reader: 입력
      - Writer: 출력

  - **생성자의 형태**에 따라 분류
    - 장식 대상 클래스
      - 어디로부터 입력받을 것인지, 어디에 쓸것인지를 나타내는 클래스
      - 4가지 클래스를 받아들이는 생성자가 없다.
      - 종류
        - 파일(File)
          - FileInputStream, FileOutputStream, FileReader, FileWriter
        - 배열(byte[], char[])
          - ByteArrayInputStream, ByteArrayOutputStream, CharReader, CharWriter
    - 장식하는 클래스
      - **다양한 입출력 방법**을 제공하는 클래스
      - 4가지 추상클래스(InputStream,OutputStreamReader,Reader,Writer)를 받아들이는 생성자가 있다.
      - 대표 종류
        - DataInputStream, DataOutputStream
        - 다양한 자료형을 읽고 쓸 수 있다.
        - PrintWriter
          - 다양하게 한 줄 출력하는 print(), println() 메소드를 제공한다.
        - BufferedReader
          - 한줄 입력받는 readLine() 메소드를 제공한다.

### try-with-resources 블럭

- close()메소드를 사용자가 호출하지 않더라도, Exception이 발생하지 않았다면 자동으로 close()가 되게 할 수 있는 방법

  - java io객체는 인스턴스를 만들고, 모두 사용하면 close()메소드를 호출해야 한다.

    ```java
    // io 객체를 닫지 않아도 된다.
    try(  // io객체를 선언
        FileInputStream fis = new FileInputStream("input.txt");
    ) { // io객체를 사용
    } catch (Exception e) {
        e.printStackTrace();
    }
    ```

### Byte 단위 입출력(1 Byte)

- Byte 단위 입출력 클래스는 클래스의 이름이 `~InputStream`, `~OutputStream`으로 끝난다.

- FileInputStream, FileOutputStream

  - **1 Byte** 단위로 파일 읽고 쓰기

    - 읽을 때는 read() 메소드를 사용한다.
    - read() 메소드는 읽은 데이터를 int 타입으로 반환한다.
      - **파일의 끝을 구분하기 위해** int(4바이트)를 반환한다.
      - 파일의 끝에 도달하면 **-1**을 반환한다.
      - 좌측 비트가 1이면 파일의 끝을 의미한다.
    - 쓸 때는 write() 메소드를 사용한다.
    - write() 메소드는 int 타입을 받는다.
      - int 타입의 **마지막 1바이트**만 파일에 쓴다.

    ```java
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        fis= new FileInputStream("input.txt");
        fos= new FileOutputStream("output.txt");
        int readData = -1;
        while((readData = fis.read()) != -1) { // 파일의 끝에 도달하면 -1을 반환한다.
            fos.write(readData); // 4바이트 중 마지막 1바이트만 쓴다.
        }
    } catch (Exception e) {
        // ...
    } finally {
        try { // 꼭 닫아야 한다.
            fis.close();
            fos.close();
        } catch(Exception e) {
            // ...
        }
    }
    ```

  - ## **여러 바이트**를 읽고 쓰기

    - 운영체제는 보통 1바이트의 데이터를 읽으려해도 512byte를 읽어들인다. 2바이트를 1바이트씩 읽으려해도 512byte를 두 번 읽어들인다.
      - 512byte만큼 읽어 들이기 위해 byte배열을 사용: `byte[] buffer = new byte[512];`

    ```java
    FileInputStream fis = null;
    FileOutputStream fos = null;
    try {
        fis= new FileInputStream("input.txt");
        fos= new FileOutputStream("output.txt");
        int readData = -1;
        byte[] buffer = new byte[512]; // 보통 512byte를 사용한다.
        while((readData = fis.read(buffer)) != -1) { // 파일의 끝에 도달하면 -1을 반환한다.
            // buffer에 데이터를 저장하고 readData에는 읽은 바이트 수를 저장한다.
            fos.write(buffer, 0, readData); // (읽은 값들, 시작 인덱스, 읽은 바이트 수)
        }
    } catch (Exception e) {
        // ...
    } finally {
        try { // 꼭 닫아야 한다.
            fis.close();
            fos.close();
        } catch(Exception e) {
            // ...
        }
    }
    ```

### 다양한 타입의 입출력(n Byte)

- DataInputStream, DataOutputStream

  - 다양한 자료형을 읽고 쓸 수 있다.
  - **DataInputStream**은 **InputStream**을 상속받고, **DataOutputStream**은 **OutputStream**을 상속받는다.
  - **데코레이션 패턴**을 사용한다.
    - 데코레이션 패턴: 기존의 클래스에 새로운 기능을 추가하기 위해 사용하는 패턴

  ```java
  // 데이터 쓰기
  try (
      DataOutputStream dos = new DataOutputStream(new FileOutputStream("output.txt"));
  ) {
      dos.writeInt(100); // int 타입의 데이터를 쓴다.
      dos.writeDouble(3.14); // double 타입의 데이터를 쓴다.
      dos.writeBoolean(true); // boolean 타입의 데이터를 쓴다.
  } catch (Exception e) {
      ex.printStackTrace();
  }

  // 데이터 읽기
  // 파일에 저장된 순서대로 읽어 들여야한다.
  try (
      DataInputStream dis = new DataInputStream(new FileInputStream("output.txt"));
  ) {
      int i = dis.readInt(); // int 타입의 데이터를 읽는다.
      double d = dis.readDouble(); // double 타입의 데이터를 읽는다.
      boolean b =  dis.readBoolean(); // boolean 타입의 데이터를 읽는다.
  } catch (Exception e) {
      ex.printStackTrace();
  }
  ```

### 문자(Char) 단위 입출력

- 문자 단위 입출력 클래스는 클래스의 이름이 `~Reader`, `~Writer`으로 끝난다.
- 키보드 입력으로부터 Console로 출력

  - `System.in`

    - 키보드로부터 입력받는다. InputStream 타입이다.
      - InputStream은 **Byte 단위**로 데이터를 읽는다.
      - `System.in`을 **문자 단위**로 읽기 위해서는 `InputStreamReader`을 사용한다.
        - `InputStreamReader`은 **문자 단위**로 데이터를 읽는다.

  - `BufferedReader`

    - 한 줄을 읽는다.

    ```java
    // Console에서의 입력
    try (
        // 데코레이션 패턴을 사용한다.
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    ) {
        String input = br.readLine(); // 한 줄을 읽는다.
    } catch (Exception e) {
        e.printStackTrace();
    }

    System.out.println(input);
    ```

- 파일에서의 입출력

  - `BufferedReader`, `FileReader`, `PrintWriter`, `FileWriter`
    - 파일에서 읽고 쓰기 위해서는 `FileReader`, `FileWriter`를 사용한다.
    - 편리하게 한 줄을 읽기 위해서 `BufferedReader`를 사용한다.
    - 편리하게 출력하기 위해서 `PrintWriter`를 사용한다.

  ```java
  // 파일에서의 입력
  try (
      // 데코레이션 패턴을 사용한다.
      BufferedReader br = new BufferedReader(new FileReader("input.txt"));
      PrintWriter pw = new PrintWriter(new FileWriter("test.txt"));

  ) {
    String line = null;
    while((line = br.readLine()) != null) { // 한 줄을 읽는다.
        pw.println(line); // 한 줄을 쓴다.
    }
  } catch (Exception e) {
      e.printStackTrace();
  }

  ```

## 어노테이션(java5부터 지원)

- 어노테이션은 **메타데이터**이다.

  - 메타데이터: 데이터를 설명해주는 데이터

- 어노테이션은 **컴파일러에게 정보를 알려주거나, 컴파일 할 때와 설치 시의 작업을 지정하거나, 실행할 때 별도의 처리가 필요할 때 사용한다.**
- 어노테이션은 **@어노테이션명**으로 사용한다.
- Custom 어노테이션

  ```java
    // 어노테이션 정의
    @Retention(RetentionPolicy.RUNTIME) //  JVM실행시에 감지
    public @interface PrintAnnotation {
        // ...
    }

    // 어노테이션 적용
    public class Service {
        @PrintAnnotation
        public void method1() {
            System.out.println("실행 내용1");
        }
    }

    // 어노테이션 실행
    public class ServiceExam {
        public static void main(String[] args) {
            Service service = new Service();
            try {
                Method method = service.getClass().getDeclaredMethod("method1");
                if(method.isAnnotationPresent(PrintAnnotation.class)) {
                    // 어노테이션이 붙으면 아래 실행
                    for(int i = 0; i < 10; i++) {
                        service.method1();
                    }
                } else {
                    // 어노테이션이 붙지 않으면 아래 실행
                    service.method1();
                }
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
  ```

## 쓰레드

- 프로세스: 실행중인 프로그램
  - ex) JVM
- 쓰레드: 프로세스 내에서 실행되는 흐름의 단위
  - 동시에 여러가지 작업을 동시에 수행할 수 있게하는 것

### 쓰레드 생성

- Thread 클래스를 상속받는 방법

  - Thread 클래스를 상속받아 `run()` 메소드를 **오버라이딩**한다.
  - Thread 클래스의 `start()` 메소드를 호출한다.

    ```java
    // Thread 클래스를 상속받는 방법
    public class MyThread extends Thread {
        String str;
        public MyThread(String str) {
            this.str = str;
        }
        @Override
        public void run() {
            for(int i = 0; i < 10; i++) {
                System.out.println(str);
                try {
                    Thread.sleep((int)(Math.random() * 1000)); // 0~999
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    // 쓰레드 실행
    public class ThreadExam {
        public static void main(String[] args) {
            MyThread t1 = new MyThread("*");
            MyThread t2 = new MyThread("-");
            // 무작위로 동시에 출력된다.
            t1.start();
            t2.start();
        }
    }
    ```

- Runnable 인터페이스를 구현하는 방법

  - Runnable 인터페이스를 구현한다.
  - Thread 클래스의 생성자에 Runnable 인터페이스를 구현한 객체를 전달한다.
  - Thread 클래스의 `start()` 메소드를 호출한다.
  - **왜 Runnable 인터페이스를 구현하는 방법을 사용하는가?**

    - **다중 상속이 불가능하기 때문에**
    - **Runnable 인터페이스를 구현하는 방법을 사용하면 다른 클래스를 상속받을 수 있다.**

    ```java
    // Runnable 인터페이스를 구현하는 방법
    public class MyThread implements Runnable {
        String str;
        public MyThread(String str) {
            this.str = str;
        }
        @Override
        public void run() {
            for(int i = 0; i < 10; i++) {
                System.out.println(str);
                try {
                    Thread.sleep((int)(Math.random() * 1000)); // 0~999
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    // 쓰레드 실행
    public class ThreadExam {
        public static void main(String[] args) {
            MyThread t1 = new MyThread("*"); // 쓰레드가 아니다.
            MyThread t2 = new MyThread("-"); // 쓰레드가 아니다.
            // 무작위로 동시에 출력된다.
            new Thread(t1).start(); // Thread를 생성
            new Thread(t2).start(); // Thread를 생성
        }
    }
    ```

### 쓰레드와 공유 객체와 동기화

- 하나의 객체(= 공유객체)를 여러 개의 Thread가 사용하는 것
- **어떤 문제가 발생할까?**

  - 자원이 공유되기 때문에 원하지 않게 값이 바뀔 수 있다.
  - 해결 방법: **동기화**를 사용한다.

- 동기화(synchronized)

  - **하나의 쓰레드가 작업을 끝낼 때까지 다른 쓰레드는 대기하게 한다.**

- 동기화 메소드

  - 메소드 선언부에 `synchronized` 키워드를 붙인다.
  - 먼저 호출한 메소드가 **공유 객체의 사용권(Monitoring Lock)**을 얻는다.

    - 메소드 실행이 종료되거나, wait()와 같은 메소드를 만나기 전까지 유지
    - 다른 쓰레드들은 모니터링 락을 놓을때까지 대기한다.
    - synchronized를 붙히지 않은 메소드는 다른 쓰레드들이 synchronized메소드를 실행하면서 모니터링 락을 획득했다 하더라도, 그것과 상관없이 실행

    ```java
    // 동기화 메소드: 공유 객체 메서드에 synchronized를 붙힌다.
    public synchronized void method() {
        // ...
    }
    ```

- 동기화 블럭

  - 메소드의 코드가 길어지면, 마지막에 대기하는 쓰레드가 너무 오래 기다리는것을 막기위해서 만들었다.
  - 문제가 있을것 같은 부분만 synchronized블록을 사용

    ```java
    // 동기화 블록
    public void method() {
        // ...
        synchronized(this) { // this는 공유 객체
            // ...
        }
        // ...
    }
    ```

### 쓰레드와 상태제어

- JVM은 시간을 쪼개서 여러 쓰레드에게 나누어 준다.
  - 이 때문에 동시에 실행되는 것처럼 보인다.
- 쓰레드의 상태
  - NEW: 쓰레드가 생성되고 아직 `start()`가 호출되지 않은 상태
  - RUNNABLE: 실행 중 또는 실행 가능한 상태
  - RUNNING: 실행 중인 상태
  - BLOCKED: 동기화 블록에 의해서 일시정지된 상태
  - DEAD: 쓰레드의 작업이 종료된 상태
- 쓰레드의 상태 제어
  - `yield()`: 실행 중인 쓰레드를 실행 대기 상태로 만든다. 다른 쓰레드에게 실행을 양보한다.
  - `sleep()`: BLOCKED 상태로 만든다.
  - `wait()`: 해당 쓰레드는 해당 객체의 모니터링 락에 대한 권한을 가지고 있다면 모니터링 락의 권한을 놓고 대기
    - wait와 notify는 동기화된 블록안에서 사용
  - `notify()`: wait()에 의해 일시정지된 쓰레드를 실행 대기 상태로 만든다.
    - wait와 notify는 동기화된 블록안에서 사용
  - `join()`: 쓰레드가 종료될 때까지 기다린다.

### 데몬 쓰레드

- 데몬(Daemon): 보통 리눅스와 같은 유닉스계열의 운영체제에서 백그라운드로 동작하는 프로그램
  - `setDaemon(true)` 메서드를 호출하면 데몬 쓰레드가 된다.
- 다른 쓰레드가 모두 종료되면 자동으로 종료

## 람다

### 람다(익명 메서드)

- 함수형 인터페이스: 메서드가 하나만 있는 인터페이스

  - ex) Runnable(`run()` 하나만 가지고 있다.), Comparable(`compareTo()` 하나만 가지고 있다.)

- **왜 사용하는가?**

  - **코드의 간결성을 위해서**
    - 메서드가 하나만 있는 인터페이스를 구현하고, 객체를 생성하는 과정을 생략할 수 있다.
    - 즉, 메서드만 전달하면 된다. JVM이 알아서 추론한다.
  - Java8에 람다식이 생기면서, 마치 **함수만 전달하는 것처럼** 간편하게 문법을 사용할 수 있게 되다.
    - 과거에는 자바는 메소드만 인자로 전달하려면 반드시 객체를 만들어서 전달해야 했다.

### 람다식으로 쓰레드 만들기

```java
public class LambdaExam1 {
        public static void main(String[] args) {
            // 원래 Thread 안에는 Runnable 인터페이스를 구현한 객체를 전달해야 한다.
            // Runnable 인터페이스를 구현한 객체를 만들기 위해서는 하나 밖에 없는 run() 메서드를 오버라이딩 해야 한다.
            // 아래는 위의 과정을 압축해서 람다식으로 만든 것이다.
            new Thread(()->{
                // run() 메서드를 오버라이딩 한다.
                for(int i = 0; i < 10; i++){
                    System.out.println("hello");
                }
            }).start();
        }
    }
```

### 람다식으로 Compare 구현하기

- Compare 인터페이스

  - 두 객체를 비교하는 인터페이스

    ```java
    public interface Compare {
            public int compareTo(int value1, int value2);
        }
    ```

- 람다식으로 표현하기

  ```java
  public class LambdaExam2 {

          public static void exec(Compare compare) {
              int k = 10;
              int m = 20;
              int value = compare.compareTo(k, m);
              System.out.println(value);
          }

          public static void main(String[] args) {
              int a = 10, b = 20;
              exec((a,b) -> {
                  return a - b;
              });
          }
      }
  ```

## Stream

> [[자바의 정석 - 기초편] ch14-15,16 스트림, 스트림의 특징](https://www.youtube.com/watch?v=7Kyf4mMjbTQ) 참고
