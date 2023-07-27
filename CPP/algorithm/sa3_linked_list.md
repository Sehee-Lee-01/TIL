# 3. 연결 리스트

## 1. Linked List 개념 설명 및 종류

데이터가 자료의 주소 값으로 서로 연결 되어있는 구조이다.

- **Array와 비교**

![Untitled](3%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%20c3fefefbc4144499bdde73692a75fefe/Untitled.png)

Array는 메모리에 데이터가 연속으로 저장됩니다.

하지만 연결 리스트는 노드 안에 다음 데이터의 주소가 저장되어있는 구조라서 메모리에 데이터가 연속으로 저장되는 경우가 아닐 수도 있습니다.

- **계산복잡도**

![Untitled](3%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%20c3fefefbc4144499bdde73692a75fefe/Untitled%201.png)

### 1.1. 단순 연결 리스트 (Singly Linked List)

![Untitled](3%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%20c3fefefbc4144499bdde73692a75fefe/Untitled%202.png)

### 1.**2. 이중 연결 리스트 (Doubly Linked List)**

![Untitled](3%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%20c3fefefbc4144499bdde73692a75fefe/Untitled%203.png)

### 1.**3. 원형 연결 리스트 (Circular Linked List)**

![Untitled](3%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%20c3fefefbc4144499bdde73692a75fefe/Untitled%204.png)

**2. Linked List의 동작**

- **데이터 삽입**

![Untitled](3%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%20c3fefefbc4144499bdde73692a75fefe/Untitled%205.png)

- **데이터 삭제**

![Untitled](3%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%85%E1%85%B5%E1%84%89%E1%85%B3%E1%84%90%E1%85%B3%20c3fefefbc4144499bdde73692a75fefe/Untitled%206.png)

**3. 정적 할당을 사용한 Linked List 구현**

- 보통은 동적 할당으로 연결 리스트를 구현하지만 알고리즘 문제를 풀 때 동적 할당을 하게 되면 성능이 떨어지고 실수할 여지가 생긴다. **문제를 풀 때 만큼은 메모리 풀을 통해 정적 할당을 해보자.**
- 정적 할당이란?
    - 사용될 노드를 한 번에 모두 할당한 다음, 필요할 때마다 하나씩 꺼내 쓰는 것이다.
    - **장점**
        - 동적 할당을 하는 **오버헤드**가 없어집니다.
        - 사용이 끝날 때마다(특히 여러 개의 테스트 케이스가 있는 경우) **메모리를 해제**할 필요가 없습니다.
        - 모든 노드가 메모리 상에서 뭉쳐 있기 때문에 **캐시 효율**이 높아집니다.

**2.2 초기화**

- 더미 노드 만들기
    - SinglyLinked List 경우에는 더미 노드 head 만들기
    - Doubly Linked List 경우에는 더미 노드 head, tail 두 개 만들기
- 큰 데이터를 연결 리스트로 저장하고자 한다면 더미 노드는 좋은 선택이 아닐 수 있음.

**2.3 삽입**

**2.4 삭제**

- 이전 노드 정보를 알 방법이 없으니 삭제는 이전 노드에서 작업이 이루어져야 한다.

**2.5 탐색**

- head 노드부터 탐색한다.
- Doubly Linked List인 경우에는 tail 노드부터 탐색도 가능하다.