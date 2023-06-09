# 14. 세그먼트 트리

- **세그먼트 트리**는 **point update와 range query**를 모두 **O(logN)**의 시간에 처리할 수 있는 자료구조입니다.
  - 시간/공간 복잡도가 매우 효율적이고, 구현이 짧고, 정말 많은 변형이 가능한, 알고리즘 문제에서의 맥가이버 칼과 같은 자료구조입니다.
- **기초적인 형태의 세그먼트 트리**란, **교환법칙이 성립하는 연산**에 대한 range query를 처리하는 세그먼트 트리를 말합니다.
  - 예를 들어, 구간 최소값이나 구간 합은 min(min(a, b), c) = min(a, min(b, c))이고, (a + b) + c = a + (b + c)이므로 min과 +연산은 둘 다 교환법칙이 성립합니다.

# 1. **수열의 구간 합을 구하기(예시)**

![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download.png)

## 1) **완전 탐색과 DP로 해결하기**

- **완전 탐색**

  ![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%201.png)

  - point update O(1), range query O(N)

- **DP**

  ![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%202.png)

  - point update O(N^2), range query O(1)

## 2) **세그먼트 트리 구조**

![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%203.png)

- 세그먼트 트리는 **완전 이진 트리**
  - **리프 노드: 구간의 길이가 1**인(원소의 개수가 하나인) 구간
  - **나머지 노드:** 자식 노드를 합친 **구간 합**
  - **노드 개수:** 2N - 1개(배열의 길이=N)
  - **높이:** O(logN)
  - 힙과 마찬가지로 세그먼트 트리는 **배열**로 구현할 수 있습니다.
    - 0번 노드는 버리고, 1번 노드가 루트가 되는 방식으로 구현
    - 필요한 배열의 길이: 2N
    - 리프 노드의 인덱스: [ N , 2N )

## 3) **Point Update**

- 원소 하나(리프 노드)가 바뀌면 그 원소를 포함하는 모든 구간(리프 노드의 모든 조상)의 값도 바뀌어야 한다.
  - i번째 리프 노드의 인덱스는 i + N
  - **그 값을 바꿔주고, 해당 리프 노드부터 루트 노드까지 부모 노드를 타고 올라가면서 조상 노드의 값을 갱신**

![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%204.png)

## 4) **Range Query**

- 구간 쿼리가 들어오면, 몇 개의 노드를 골라서 해당 구간을 정확히 덮어야 합니다.

![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%205.png)

![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%206.png)

![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%207.png)

- **구간의 시작점 노드 l**과 **구간의 끝점의 다음 노드 r**에서 부모 노드로 올라가면서, 해당 노드에 적힌 값을 결과값에 더해야 하면 더하고, 아니라면 건너뛰는 작업을 반복합니다.
  - l노드의 위치에 따른 계산
    - 왼쪽 그림처럼 **부모 노드의 왼쪽 자식일 경우**(인덱스가 짝수일 경우), 굳이 저기 적힌 값을 더할 필요가 없습니다. **부모 노드 p에 적힌 값을 더하면 l 뿐만 아니라 오른쪽 자식의 값도 한 번에 더할 수 있으므로 건너뜁니다.**
    - 부모 노드의 **오른쪽 자식일 경우**(인덱스가 홀수일 경우), 지금 더하지 않고 부모 노드로 올라가게 되면 **구간에 포함되지 않는 왼쪽 자식의 값이 섞이게 됩니다.** 따라서 **l에 적힌 값을 더하고 구간에서 l 노드를 제외하면 됩니다.**
  - **r 노드**도 같은 논리로 부모 노드로 계속 올라가면서 필요할 때만 값을 더해주면 됩니다.

# 2. **기타**

- 위에서 만든 세그먼트 트리는 노드 순서가 뒤죽박죽입니다. 왼쪽 자식이 오른쪽 구간을, 오른쪽 자식이 왼쪽 구간을 나타내는 경우도 있고 중간이 끊긴 구간을 나타내는 노드도 있습니다.
- **교환법칙이 성립하지 않는** 일반적인 연산인 경우

  - 노드가 나타내는 구간이 **정렬 상태**를 유지해야 합니다.
  - **비재귀적 방식** 구현

    - **포화 이진 트리**로 만들기 위해 **리프 노드의 개수가 2의 거듭제곱**이 되어야 하므로 **더미 노드**를 둡니다.

      ![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%208.png)

  - **재귀적 방식** 구현

    - 포화 이진 트리는 아니다.
    - **리프 노드** **순서**만 조정

      ![download.png](14%20%E1%84%89%E1%85%A6%E1%84%80%E1%85%B3%E1%84%86%E1%85%A5%E1%86%AB%E1%84%90%E1%85%B3%20%E1%84%90%E1%85%B3%E1%84%85%E1%85%B5%2060f186205d7a40d2b45f111fe02ed9d8/download%209.png)
