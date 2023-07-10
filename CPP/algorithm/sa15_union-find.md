# 15.Union-Find

![Untitled](15%20Union-Find%205359bca86ddd4551b1d4d98332109455/Untitled.png)

- **그래프 알고리즘**으로 두 노드가 **같은 그래프**에 속하는지 판별하는 알고리즘이다.
  - 서로소 집합, 상호 배타적 집합(Disjoint-Set)으로도 불린다.
- **트리 구조**로 이루어진 **자료구조 중 하나**로 생각되기도 한다.
- **2개의 Operation**

| Union(a, b) | Find(a) |
| ----------- | ------- |

| • a 그룹과 b 그룹을 union
• Tree 구조 형태로 union 수행 | a 그룹의 루트 노드를 탐색 |

- 특징
  - 특정 노드가 어느 집단에 속하는지 알 수 있다.
  - 트리의 구조를 사용하면 Find의 시간복잡도가 평균적으로 O(logN)이지만, 편향될 경우 O(N)이 될 수 있다.
    - **경로 압축(Pass Compression)**을 통해 상수에 가깝게 만들 수 있다.

# 1. **Operation**

- **Union**

  ![Untitled](15%20Union-Find%205359bca86ddd4551b1d4d98332109455/Untitled%201.png)

  - 노드 a와 노드 b를 합친다.
  - a의 루트와 b의 루트를 부모로 연결한다.

- **Find**

  ![Untitled](15%20Union-Find%205359bca86ddd4551b1d4d98332109455/Untitled%202.png)

  - 노드 x의 **루트**를 찾는다.
  - **부모 노드**가 **자기 자신**일 때까지 타고 올라간다.

# 2. **경로 압축(Pass Compression)**

![Find 수행 시 최악의 상황](15%20Union-Find%205359bca86ddd4551b1d4d98332109455/Untitled%203.png)

Find 수행 시 최악의 상황

- 루트를 찾는 경우 최악의 상황에서는 O(N)만큼의 계산이 요구된다.
  - **경로 압축(Pass Compression)을 통해 해결 가능!**
- Find는 Depth가 낮을 수록 유리하다는 것이 포인트
  - 매번 Find 할 때 Depth가 2 이상이면 경로 압축 수행
  ```cpp
  int Find(int x)
  {
  	//Depth가 0인 경우
  	if (x == parent[x]) return x;
  	return parent[x] = Find(parent[x]); // root를 찾아서 x의 부모 값으로 변경
  }
  ```
  ![Untitled](15%20Union-Find%205359bca86ddd4551b1d4d98332109455/Untitled%204.png)
