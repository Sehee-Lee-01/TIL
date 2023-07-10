# 2. 비트연산

## **2.1 비트(bit)**

- 1bit = 0 or 1
- 8bits = 1byte

## **2.2 비트 연산자**

| 비트 연산자 |              | a = 0b1010, b = 0b0100   |
| ----------- | ------------ | ------------------------ |
| &           | AND          | a & b = 0b0000           |
| ^           | XOR          | a ^ b = 0b1110           |
| ~           | NOT          | ~a = 0b0101              |
| <<          | 왼쪽 Shift   | a << n = a \* pow(2, n)  |
| >>          | 오른쪽 Shift | a >> n = a \* pow(2, -n) |

> OR은 |로 표시한다

<aside>
📢 *연산자 우선순위:*  사칙연산 > 비교 연산 > **비트 연산** > 논리 연산

</aside>

<aside>
💡  **0b** : 이진수를 표현할 때 앞에 붙는 표현

</aside>

## **2.3 비트 연산 응용**

- **& AND, | OR**
  - 교집합, 합집합
- **^ XOR**
  - true/false를 번갈아 바꾸는 스위치를 구현
  - 대소문자 변환 함수
  ```cpp
  char case_convert(char alphabet) {
  	return alphabet ^ 32;
  }
  ```
  - 같은 값끼리 XOR하면 0이 되는 특징

<aside>
❓ 이 부분은 헷갈리니 **XOR** 나올 때마다 잘 보자.

</aside>

- **~ NOT**
  - 가지고 있지 않은 원소들을 구할 수 있다.
  - 음의 인덱스
- **<<, >> shift**
  - 2의 거듭제곱 곱셈/나눗셈

## **2.4 비트마스킹**

- 각 Bit를 하나의 Flag로 활용
  - 자료 저장과 집합 표현

## **2.5 데이터 압축**

```cpp
// 12자 이내의 알파벳 대문자 문자열을 하나의 long long 변수에 압축
// WARNING 문자열의 끝(‘\0’) 이후에도 전부 ‘\0’으로 채워져 있어야 함
long long compress(char str[13]) {
	long long res = 0;
	for (size_t i = 0; i < 12; ++i) {
		res = (res << 5) | (str[i] ^ 64);
	}
	return res;
}
```

## **3. 기본 문제**

- [문제1](https://github.com/Sehee-Lee-01/samsung_dx_algorithm/tree/main/study/day2)
