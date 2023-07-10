# 9. 해시

# 1. **해시 테이블**

![download.png](9%20%E1%84%92%E1%85%A2%E1%84%89%E1%85%B5%204498ebab552a42e6a551bfebd4187dd0/download.png)

- **Value** : 저장하고자 하는 정보. 최종적으로 저장소(bucket, slot)에 hash와 매칭되어 저장됩니다.
- **key** : 고유한 값. Hash function의 input입니다. Key값 그대로 최종 저장소에 저장되면 ,다양한 길이의 저장소를 미리 구성해 두어야 하기 떄문에 hash function으로 값을 바꿔 저장합니다.
- **Hash function** : key를 고정된 길이의 hash로 변경합니다. 이때 서로 다른 key가 같은 hash가 되는 경우가 있습니다. 이를 Hash Collison 이라 불리며, Hash Collision 발생 확률을 최대한 줄이는 Hash function을 만들어야 합니다. **Hash Collision**을 해결하는 방법에는 **chaining 기법** 과 **open address hash 방식**이 있습니다.

# 2. **Hash Table의 삽입, 삭제, 검색**

- 삽입, 삭제, 검색의 시간 복잡도는 O(1): Hash Collision을 고려하지 않았을 떄
- 최악의 경우는 O(n)

# 3. **hash function example - djb2**

```cpp
unsigned long djb2(unsigned char* str)
{
            unsigned long hash = 5381;
            int c;
            while (c = *str++)
						{
              // hash * 33 + c
							hash = ((hash << 5) + hash) + c;
            }
            return hash;
}
```

- djb2는 문자열의 hash 함수 중 간략하면서도 무작위 분포를 만드는데 뛰어나다고 알려져 있습니다.
- magic number 5381과 33을 활용하여 hash key를 생성

# 4. **Hash Collision(충돌)**

- 입력 값이 달라도 해시 값은 같을 수 있기 때문에 충돌의 가능성은 늘 존재

**◆ Open addressing**

- 충돌이 발생할 경우, 해시 테이블의 다른 자리에 대신 저장하는 방법
- 하나의 해시에 하나의 값이 매칭됩니다.
- 비어있는 해시를 찾는 규칙에 따라 다음과 같이 구분할 수 있습니다.
  - **선형 탐색(Linear Probing):** 다음 해시(+1)나 n개(+n)를 건너뛰어 비어있는 해시에 데이터를 저장
  - **제곱 탐색(Quadratic Probing):** 충돌이 일어난 해시의 제곱을 한 해시에 데이터를 저장
  - **이중 해시(Double Hashing):** 다른 해시 함수를 한 번 더 적용한 해시에 데이터를 저장

◆ **Chaining**

![download.png](9%20%E1%84%92%E1%85%A2%E1%84%89%E1%85%B5%204498ebab552a42e6a551bfebd4187dd0/download%201.png)

- **Linked list**를 이용해서 충돌을 해결하는 방법(주로 사용할 방법)
- 자료 저장시, 저장소(bucket)에서 충돌이 일어나면 해당 값을 기존 값과 연결
- **장점**
  - 한정된 저장소(Bucket)를 효율적으로 사용할 수 있습니다.
  - 상대적으로 적은 메모리를 사용합니다
- **단점**
  - 한 Hash에 자료들이 계속 연결될 수 있으며, 이때 검색 효율이 떨어집니다.

# 5. **적절한 hash table size**

- 보통 소수나 2의 거듭제곱(2^m)을 사용

# 6. **생일 문제 예제**

- 무조건 해시 테이블의 크기를 충분히 크게 만드는 방법이 얼마나 비효율적인지 알려주는 문제
- 충돌 확률 100%
  - 비둘기 집의 원리에 의해 366명의 사람이 모이면 생일이 같은 쌍이 무조건(100%) 생긴다.
- 충돌 확률 50%
  - 생일이 같은 쌍이 존재할 확률이 50%가 되기 위해서는 23명이 필요.
    ![Untitled](9%20%E1%84%92%E1%85%A2%E1%84%89%E1%85%B5%204498ebab552a42e6a551bfebd4187dd0/Untitled.png)
  - 크기가 365인 해시 테이블에 23개(테이블 크기의 겨우 6.3%입니다)의 데이터만 삽입해도 충돌이 일어날 확률이 50%가 넘는다.
    **⇒ 무조건 크기가 크다고 좋은 건 아니다.**
