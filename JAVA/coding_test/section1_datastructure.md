# 자료구조

> [Do it! 알고리즘 코딩테스트 with JAVA](https://inf.run/yax9)를 수강하며 기록했습니다.

## 1. 배열과 리스트

### 1) 구간 합

- 합 배열을 이용하여 시간복잡도를 줄인다.
- **변형이 자주 되는 배열**의 구간 합을 구하려면 **세그먼트 트리**를 알아야한다.

### 2) 예제

- #### `배열과 리스트` 백준 11720

  - 100자리 input은 숫자 자료형으로 받지 못한다. → String으로 받자.
  - 긴 String을 나누고 싶다 → `toCharArray()`를 사용하여 나누자.
  - char을 int로 바꾸고 싶다. → ASCII 코드를 알아야한다.
  - 값을 두 개만 입력 받는 경우에는 `Scanner`를 사용하자.

  ```java
      Scanner sc = new Scanner(System.in)
      int N = sc.nextInt()
      String str = sc.next()
  ```

- #### `배열과 리스트` 백준 1546

  - 계산식이 있으면 한 번에 계산할 수 있는지도 확인해본다.

- #### `구간 합` 백준 11659

  - 가장 큰 데이터(최악의 경우)가 들어간다고 생각하고 시간 복잡도 생각해보자.

    - 배열 100,000 \* 질의 100,000 = 10,000,000,000(1억이 넘어간다.)

      - 0.5초 안에 풀 수 있는 알고리즘을 생각해야한다. → 구간 합

  - input 값이 많을 때는 `BufferedReader` 사용하자.(더 빠르다.)
  - 한 줄에 정보가 많을 때는 StringTokenizer 사용한다.
  - 덧셈, 곱셈 많을 때는 `long`형으로 선언해주자.

- #### `투 포인터` 백준 2018

  - N의 최댓 값이 매우 크므로 알고리즘 선택에 유의하자!
  - 배열 저장 방법도 있지만 투 포인터 방법도 있다.
    - O(N)에 해결할 수 있다.

- #### `투 포인터` 백준 1940

  - 투포인터의 위치 지정을 신경쓰자.
  - java는 Array를 정렬하는 도구를 지원해준다. `Arrays.sort(arr)`

- #### `슬라이딩 윈도우` 백준 12891

  - 문제를 먼저 생각하고 구현하자.
  - 범위 = 윈도우

## 2. 스택과 큐

### 1) 예제

- #### `스택과 큐` 백준 1874

  - `Stack` 라이브러리 사용하기

  ```java
  import java.util.Stack;

  Stack<Integer> stack = new Stack<>();
  stack.push(1);
  stack.pop();
  ```

- #### `스택과 큐` 백준 2164

  - `Queue` 라이브러리 사용하기

  ```java
    import java.util.Queue;
    import java.util.LinkedList;
    Queue<Integer> queue = new LinkedList<>();
  ```

- #### `스택과 큐` 백준 11286

  - 문제 이해가 안될 땐 입출력으로 예상해보자.

  - `PriorityQueue` 라이브러리 구현하기

  ```java
  PriorityQueue<Integer> pq = new PriorityQueue<>();
  ```

  - `PriorityQueue` 우선순위 큐 정렬 커스터마이징(절댓값으로 우선순위를 정할 때)

  ```java
  PriorityQueue<Integer> pq = new PriorityQueue<>(
            // "양수" 리턴시 스왑
            (o1, o2) -> {
                if(Math.abs(o1) == Math.abs(o2)) return o1 - o2;
                else return Math.abs(o1) - Math.abs(o2);
            }
    );
  ```
