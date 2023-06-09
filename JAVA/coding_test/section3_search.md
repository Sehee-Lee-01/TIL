# 탐색

> [Do it! 알고리즘 코딩테스트 with JAVA](https://inf.run/yax9)를 수강하며 기록했습니다.

## 1. DFS(깊이 우선 탐색)

### 1) DFS

- `재귀함수`나 `스택` 구조를 사용한다.
  - 재귀함수는 `스택오버플로`를 조심해야한다.
- O(V + E) → V: 노드 수, E: 엣지 수
- 노드를 2번 이상 방문하면 안되므로 방문 체크 배열이 필요하다.
- 3단계
  1. 시작 노드 정하고, 자료구조 초기화
     - 방문한 노드는 다시 방문을 안하므로 방문 체크 배열이 필요하다.
  2. 스택에서 노드를 꺼내고 그 노드의 인접 노드들을 스택에 삽입
  3. 스택에 노드가 없을 때까지 진행한다.

### 2) 예제

- #### `DFS` 백준 11724
  - 노드 최대 개수가 1000개이므로 N^2이하의 모든 알고리즘 사용이 가능하다.
  - ArrayList와 LinkedList 차이[(참고링크)](https://dev-coco.tistory.com/19)
    - ArrayList는 조회가 많을 때, LinkedList는 삽입, 삭제가 많을 때 사용하자.

## 2. BFS(너비우선탐색)

### 1) BFS

- 시작 노드를 기준으로 `가까운 노드`를 먼저 방문하며 탐색

  - 선입 선출, `큐`를 이용한다.
  - 도착 경로가 여러 개 일 때 최단 경로를 보장한다.

- 3단계
  1. 시작 노드 정하고, 자료구조 초기화
     - 방문한 노드는 다시 방문을 안하므로 방문 체크 배열이 필요하다.
  2. 큐에서 노드를 꺼내고 그 노드의 인접 노드들을 큐에 삽입
  3. 큐에 노드가 없을 때까지 진행한다.

### 2) 예제

- #### `BFS` 백준 2178

  - 100정도면 시간복잡도 무시하고 풀어도 되는 정도이다!
  - 시간 제한보다는 최단 거리를 원하기 때문에 완전탐색 가능 → BFS or DFS
  - 둘 다 풀 수 있지만 해당 깊이에서 `찾는 순간 바로` 그 값이 최솟값이기 때문에 BFS가 적합하다.
  - 나는 일일이 상하좌우 조건을 4번 계산했지만 상하좌우 배열을 만들어서 간편하게 구현할 수 있다.

  ```java
  // 상하좌우
  int[] dx = {0,1,0,-1};
  int[] dy = {1,0,-1,0};

  ```

  - 그리고 나는 visited 배열을 선언하지않고 바로 2차원 배열에 업데이트 된 값을 입력하여 그 값이 양수이면 방문을 했다고 가정하고 풀었는데 visited 배열 방법도 적합한 때에 써봐야겠다.
  - String을 한 글자씩 잘라야하는 경우 방법
    ```java
    String str = "12345"
    // 1, String 리턴
    String substr = str.substring(0, 1); // "1"
    // 2, char 리턴
    char[] strlist = str.toCharArray();
    char c = strlist[0]; // '1'
    // 3, char 리턴
    char c = str.charAt(0); // '1'
    ```

## 3. Binary Search(이진 탐색)

### 1) Binary Search

- 데이터가 정렬되어 있는 상태에서 적용할 수 있다.
- 데이터 셋의 중앙값을 이용하여 구현한다.

### 2) 예제

- #### `Binary Search` 백준 1920
  - 시간복잡도 예상하기!
    - 단순 반복문으로는 문제를 풀 수 없다.
  - sort를 해야하는 상황이라면 ArrayList가 나을까 LinkedList가 나을까
    - 자바8 기준으로는 ArrayList가 낫다고 한다.[참고링크](https://stackoverflow.com/questions/8069370/is-an-arraylist-or-a-linkedlist-better-for-sorting)
    - 바로 쓸 수 있는 배열인지 다 저장 해놓고 써야하는 배열인지 생각하기
    - StringBuffer/StringBuilder 무엇을 써야할까?[참고링크](https://ifuwanna.tistory.com/221)
      - 동기화의 유뮤가 큰 차이이다. 멀티 스레드 환경에서 안전한 것은 `StringBuffer`. 하지만 코딩테스트처럼 단일 스레드 환경에서 구현하는 경우에는 동기화를 지원하지는 않지만 `StringBuilder`가 성능이 더 낫다.
