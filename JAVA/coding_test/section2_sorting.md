# 정렬

> [Do it! 알고리즘 코딩테스트 with JAVA](https://inf.run/yax9)를 수강하며 기록했습니다.

## 1. 버블 정렬(Bubble sort)

- 데이터의 **인접 요소**끼리 비교하고, **swap** 연산을 수행하여 정렬
- O(n^2)

## 2. 선택 정렬(Selection sort)

- 대상에서 **가장 크거나 작은 데이터**를 찾아가 선택을 반복하면서 정렬
- O(n^2)

## 3. 삽입 정렬(Insertion sort)

- 대상을 선택해 **정렬된 영역**에서 선택 데이터의 **적절한 위치**를 찾아 삽입하며 정렬
- O(n^2)

## 4. 퀵 정렬(Quick sort)

- pivot 값을 선정해 해당 값을 기준으로 정렬
- O(nlogn)
- 재귀 개념이 들어간다.
- 구성요소 및 과정 예시: 투포인터
  - pivot(기준 값)
  - start: pivot보다 큰값이 나올 때까지 pivot과 비교함
  - end
    - start에서 pivot보다 큰 값이 나왔을 때 pivot보다 작은 값이 나올 때까지 pivot과 비교
    - 그 후 pivot보다 작은 값이 나오면 start와 swap

## 5. **병합 정렬(Merge sort)**

- 이미 정렬된 부분 집합을 효율적으로 병합해 전체를 정렬
- O(nlogn)
- 핵심 이론이 자주 나온다!
- **투 포인터로 두 그룹을 병합 정렬한다.**

## 6. 기수 정렬(Radix sort)

- 데이터의 자릿수를 바탕으로 비교해 데이터를 정렬
- O(kn): k는 자릿수
- 값을 비교하지 않고 자릿수를 정한 다음 해당 자릿수만을 비교하며 정렬한다.
  - 오름차운으로 하고 싶으면 작은 자릿수 부터 비교
- 데이터의 자릿수가 짧을 때 이용하면 좋다.
- 각 자릿수마다 큐를 만들어서 이용한다.
