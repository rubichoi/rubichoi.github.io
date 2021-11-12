소수 찾기

https://programmers.co.kr/learn/courses/30/lessons/42839

a |= b : a와 b의 비트를 OR 연산한 후 결과를 a에 할당

## 에라토스 테네스의 체

고대 그리스 수학자 에라토스테네스가 만들어 낸 소수를 찾는 방법. O(Nlog(logN))의 시간 복잡도를 가진다.

k=2부터 √n 이하까지 반복하여 자연수들 중 k(제외되지 않았다면)를 제외한 k의 배수들을 제외시킨다.

## 순열과 조합 라이브러리

1. 순열(permutations)
- permutations(반복 가능한 객체, n) // n=몇개를 뽑을 것인지

중복을 허용하지 않는다.
순서에 의미가 있다 (= 같은 값이 뽑히더라도 순서가 다르면 다른 경우의 수로 판단)


```python
from itertools import permutations

print(list(permutations([1,2,3,4], 2)))
print(list(permutations([1,2,3,1], 2)))
```

    [(1, 2), (1, 3), (1, 4), (2, 1), (2, 3), (2, 4), (3, 1), (3, 2), (3, 4), (4, 1), (4, 2), (4, 3)]
    [(1, 2), (1, 3), (1, 1), (2, 1), (2, 3), (2, 1), (3, 1), (3, 2), (3, 1), (1, 1), (1, 2), (1, 3)]
    

2. 중복 순열(product)
- product(반복 가능한 객체, repeat=num)

중복을 허용하는 순열


```python
from itertools import product

print(list(product([1,2,3,4], repeat=2)))
print(list(product([1,2,3,1], repeat=2)))
```

    [(1, 1), (1, 2), (1, 3), (1, 4), (2, 1), (2, 2), (2, 3), (2, 4), (3, 1), (3, 2), (3, 3), (3, 4), (4, 1), (4, 2), (4, 3), (4, 4)]
    [(1, 1), (1, 2), (1, 3), (1, 1), (2, 1), (2, 2), (2, 3), (2, 1), (3, 1), (3, 2), (3, 3), (3, 1), (1, 1), (1, 2), (1, 3), (1, 1)]
    

3. 조합(combinations)
- combinations(반복 가능한 객체, n) // n=몇개를 뽑을 것인지

중복을 허용하지 않는다.
순서에 의미가 없다 (= 같은 값이 뽑히면 같은 경우의 수로 판단)


```python
from itertools import combinations

print(list(combinations([1,2,3,4], 2)))
print(list(combinations([1,2,3,1], 2)))

```

    [(1, 2), (1, 3), (1, 4), (2, 3), (2, 4), (3, 4)]
    [(1, 2), (1, 3), (1, 1), (2, 3), (2, 1), (3, 1)]
    

4. 중복 조합(combinations_with_replacement)
- combinations_with_replacement(반복 가능한 객체, n) // n=몇개를 뽑을 것인지

중복을 허용하는 조합


```python
from itertools import combinations_with_replacement

print(list(combinations_with_replacement([1,2,3,4], 2)))
print(list(combinations_with_replacement([1,2,3,1], 2)))
```

    [(1, 1), (1, 2), (1, 3), (1, 4), (2, 2), (2, 3), (2, 4), (3, 3), (3, 4), (4, 4)]
    [(1, 1), (1, 2), (1, 3), (1, 1), (2, 2), (2, 3), (2, 1), (3, 3), (3, 1), (1, 1)]
    

- permutations(순열)을 사용해 문제 풀이
- ''.join(map(str,arr[j])) 를 사용해 tuple을 join
- 소수를 찾는 반복문에서 범위를 2~sqrt(n) 로 지정


```python
import math
from itertools import permutations

def is_prime_number(n):
    """소수판별 함수"""
    if n==0 or n==1:                                # 0,1 은 소수가 아님
        return False
    else:
        for i in range(2, int(math.sqrt(n)) + 1):   # sqrt(n)까지만 for문을 돌면서 확인하면 된다.
            if n % i == 0:                          # 2~sqrt(num)까지 나누어 떨어지는 숫자가 있으면 소수가 아님
                return False
        
        return True                                 # for문을 다 돌았는데도 False가 아니면 소수

def solution(numbers):
    answer = []
    for i in range(1, len(numbers)+1):              
        arr = list(permutations(numbers, i))        # permutations(순열)을 사용해 i개씩 묶어지는 list 생성
        for j in range(len(arr)):                   # 생성한 list(arr) 길이만큼 for문 실행
            num = int(''.join(map(str,arr[j])))     # list(arr)의 값들은 tuple들로 되어있으모 join(map(str,))을 사용해 join해준다
            if is_prime_number(num):                
                answer.append(num)                  # is_prime_number() 함수가 True일 경우 (= 소수일 경우) num 추가
    
    answer = list(set(answer))                      # 같은 값이 나올 수 있기 때문에 set()을 통해 중복값 제거
    return len(answer)
    

print(solution("17"))       # result : 3
print(solution("011"))      # result : 2
```

    3
    2
    
