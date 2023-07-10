# 1. STL

## 1. ****Sequence containers****

- **순차적**으로 저장

| 종류 | 특징 |
| --- | --- |
| vector | • 메모리 상에서 데이터가 연속적으로 위치하는 배열
• 배열의 크기를 런타임에서 조정 가능(중간에 변경 가능)
• 포인터 종류
    1. 배열의 시작 주소
    2. 다음에 데이터가 삽입될 주소
    3. 배열의 끝 주소 |
| array | • 메모리 상에서 데이터가 연속적으로 위치하는 배열
• 배열의 크기는 컴파일 타임에 결정(중간에 변경 불가능) |
| deque | • 앞, 뒤로 데이터를 빠르게 삽입/삭제할 수 있는 double-ended-queue
• 여러 버퍼에 데이터를 나누어 저장(연속적이지 않다.) |
| list | • linked list
• 앞, 뒤 원소 주소를 알 수 있다.(뒤 원소, 해당 원소 삭제 가능) |
| forward_list | • singly-linked list
• 뒤 원소 주소만 알 수 있다.(뒤 원소만 삭제 가능) |

## 2. ****Associative containers****

- **정렬**된 상태로 유지
- Red-Black Tree
    - 자가 균형 이진 탐색 트리(self-balancing binary search tree)

| 종류 | 특징 |
| --- | --- |
| set | • 데이터 자체를 key로 사용
• key(데이터)를 기준으로 데이터 정렬 |
| multiset | • key 중복 허용 |
| map | • key, value 쌍을 받아서 사용
• key를 기준으로 데이터 정렬 |
| multimap | • key 중복 허용 |

## 3. ****Unordered associative containers****

- **해시값**을 사용하여 저장
    - 데이터의 순서가 상관 없을 때 이용
    - 해시 충돌 주의

| 종류 | 특징 |
| --- | --- |
| unordered_set | • 데이터 자체를 key로 사용
•  key(데이터)의 정렬이 중요하지 않을 때 이용 |
| unordered_multiset | • key 중복 허용 |
| unordered_map | • key, value 쌍을 받아서 사용
• key의 정렬이 중요하지 않을 때 이용
• 각 버킷마다 linked list로 (key, value) 쌍을 저장 |
| unordered_multimap | • key 중복 허용 |

## 4. ****Container adaptors****

- std library에 실제로 구현되어 있지 않다.
    - 인터페이스만 제공

| 종류 | 특징 |
| --- | --- |
| stack | • LIFO |
| queue | • FIFO |
| priority_queue | • Container를 max heap으로 유지
• 최댓값, 최솟값을 빠르게 찾을 수 있다. |

## 🔗 참고링크

- [https://en.cppreference.com/w/cpp/container](https://en.cppreference.com/w/cpp/container)
- [https://skstormdummy.tistory.com/entry/%EC%9A%B0%EC%B8%A1-%EA%B0%92-%EC%B0%B8%EC%A1%B0-RValue-Reference](https://skstormdummy.tistory.com/entry/%EC%9A%B0%EC%B8%A1-%EA%B0%92-%EC%B0%B8%EC%A1%B0-RValue-Reference)