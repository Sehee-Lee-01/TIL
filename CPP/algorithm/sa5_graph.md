# 5. 그래프

```cpp
constexpr int n = 5;
const std::vector< std::pair< int, int >> edges = {{0, 1}, {0, 2}, {0, 3}, {1, 2}, {1, 4}, {3, 2}, {4, 3}};
```

![Untitled](5%20%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B3%205ab915ea89f54ea6bad2af1a3c33a512/Untitled.png)

# 1. 인접 행렬(2차원 std::vector)

```cpp
constexpr int n = 5;
const std::vector< std::pair< int, int >> edges = {{0, 1}, {0, 2}, {0, 3}, {1, 2}, {1, 4}, {3, 2}, {4, 3}};

std::vector< std::vector< int >> graph(n);
for (const auto& e : edges) {
	graph[e.first].emplace_back(e.second);
}
```

![Untitled](5%20%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B3%205ab915ea89f54ea6bad2af1a3c33a512/Untitled%201.png)

- 가장 간단하게 구현 가능
- 동적 할당으로 push하는 데 오버헤드 가능성 있음
- 메모리에 빈 공간 생성(vector capacity)
- 배열이 파편화되어 저장되므로 캐시 효율이 떨어짐

# 2. 인접 리스트

```cpp
constexpr int n = 5;
const std::vector< std::pair< int, int >> edges = {{0, 1}, {0, 2}, {0, 3}, {1, 2}, {1, 4}, {3, 2}, {4, 3}};

struct LinkedListNode {
	int id;
	int next;
};
std::vector< LinkedListNode > nodes(edges.size());
std::vector< int > head(n, -1);
for (int i = 0; i < static_cast< int >(edges.size()); ++i) {
	nodes[i].id = edges[i].second;
	nodes[i].next = head[edges[i].first];
	head[edges[i].first] = i;
}
```

![Untitled](5%20%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B3%205ab915ea89f54ea6bad2af1a3c33a512/Untitled%202.png)

- std::vector를 대신하는 방법
- 정점마다 인접한 정점의 개수는 미리 알지 못하지만, 총 간선의 개수는 알고 있으므로 사용할 메모리만 정확하게 미리 할당 가능
- 메모리를 효율적으로 사용
- 정점 정보를 연결 리스트에 저장하므로 정렬하거나 삭제하는 데 어려움
- **연결 리스트 순회는 기본적으로 배열보다 느립니다.**

# 3. 1차원 배열

```cpp
constexpr int n = 5;
const std::vector< std::pair< int, int >> edges = {{0, 1}, {0, 2}, {0, 3}, {1, 2}, {1, 4}, {3, 2}, {4, 3}};

std::vector< int > outdegree(n); // 갈 수 있는 노드 개수
std::vector< int > prefix(n + 1); // 간선 총 누적 개수
std::vector< int > vertices(edges.size()); // 간선 정보들...
for (const auto& e : edges) {
	++outdegree[e.first];
}
std::partial_sum(outdegree.begin(), outdegree.end(), std::next(prefix.begin()));
for (const auto& e : edges) {
	// 노드의 개수, 간선의 개수 계산하여 일렬로 저장
	vertices[prefix[e.first] + --outdegree[e.first]] = e.second;
}
```

![Untitled](5%20%E1%84%80%E1%85%B3%E1%84%85%E1%85%A2%E1%84%91%E1%85%B3%205ab915ea89f54ea6bad2af1a3c33a512/Untitled%203.png)

- 2차원으로 놓인 여러 개의 정점 리스트를 일렬로 잇는 방법
- 캐시 효율이 가장 뛰어남
- 크기가 다른 세 개의 독립된 배열을 사용하므로 실수할 여지 많음
- 실시간으로 간선을 추가/삭제 할 수 없음