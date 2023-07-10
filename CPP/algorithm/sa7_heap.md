# 7. 힙

# 1. 힙

- **우선순위 큐**를 위해 만들어진 자료구조
- 모든 노드에 대해서 부모와 자식 간에 일정한 대소 관계가 성립하는 **완전이진트리**
- 부모가 가지는 값은 자식보다 무조건 크거나 작아야 합니다.
  - **최대 힙**
    - 부모가 자식보다 큰 값
  - **최소 힙**
    - 부모가 자식보다 작은 값
- 전체 자료를 정렬하는 것이 아니라 **가장 큰 값(작은 값)만 몇 개 필요한 경우** 주로 사용
- **삼성 알고리즘 역량 테스트 pro B형 시험에서 단골로 나오는 자료구조**

# 2. **배열을 이용한 힙 구현**

- 힙은 완전이진트리이므로 배열로 구현이 가능하다.

![download.png](7%20%E1%84%92%E1%85%B5%E1%86%B8%207632fbc4917f441b891495380c9e0437/download.png)

![download.png](7%20%E1%84%92%E1%85%B5%E1%86%B8%207632fbc4917f441b891495380c9e0437/download%201.png)

◆ 루트 노드의 인덱스가 1로 시작하는 경우 (0번 노드는 버림)

- 부모의 인덱스 = (자식의 인덱스) / 2
- 왼쪽 자식 인덱스 = (부모의 인덱스) \* 2
- 오른쪽 자식 인덱스 = (부모의 인덱스) \* 2 + 1

## 1) 삽입: O(logN)

![download.png](7%20%E1%84%92%E1%85%B5%E1%86%B8%207632fbc4917f441b891495380c9e0437/download%202.png)

- 배열의 맨 마지막에 데이터를 삽입
- 힙 구조를 계속 유지하도록 부모와 값을 바꾸면서 올라갑니다.(Bubble up)

## 2) 삭제: O(logN)

![download.png](7%20%E1%84%92%E1%85%B5%E1%86%B8%207632fbc4917f441b891495380c9e0437/download%203.png)

- 루트 노드에 위치하는 제일 큰 데이터(최소 힙일 경우 제일 작은 데이터)를 제거한 뒤 맨 마지막 데이터를 루트 노드로 옮긴다.
- 힙 구조를 계속 유지하도록 자식과 값을 바꾸면서 내려갑니다.(Bubble down)

# 3. STL

- 간단한 구현

```cpp
#include <queue>
using namespace std;

// 최대힙1
priority_queue<int> pq_max1;

// 최대힙2
priority_queue<int, vector<int>, greater<int>> pq_max2;

// 최소힙
priority_queue<int, vector<int>, less<int>> pq_min;

// 삽입
pq_min.push(1);
pq_min.push(2);

//삭제(pop)
pq_min.pop(); // 1 pop

// 최솟값
pq_min.top(); // 2

// 비었는지 확인
pq_min.empty(); // false
```

- 구조체 사용한 구현

```cpp
#include <queue>
using namespace std;

struct TwoNum {
	int x, y;
};

struct Compare {
		bool operator()(const TwoNum &a, const TwoNum &b) {
	// 합의 크기가 큰 것이 먼저 pop 된다.
	return a.x + a.y > b.x + b.y;
	}
};

priority_queue<TwoNum , vector<TwoNum >, Compare> pq;
```
