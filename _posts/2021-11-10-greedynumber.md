큰 수 만들기

https://programmers.co.kr/learn/courses/30/lessons/42883

문제 설명

어떤 숫자에서 k개의 수를 제거했을 때 얻을 수 있는 가장 큰 숫자를 구하려 합니다.

예를 들어, 숫자 1924에서 수 두 개를 제거하면 [19, 12, 14, 92, 94, 24] 를 만들 수 있습니다. 이 중 가장 큰 숫자는 94 입니다.

문자열 형식으로 숫자 number와 제거할 수의 개수 k가 solution 함수의 매개변수로 주어집니다. number에서 k 개의 수를 제거했을 때 만들 수 있는 수 중 가장 큰 숫자를 문자열 형태로 return 하도록 solution 함수를 완성하세요.

- 탐욕법

현재 상황에서 가장 좋아 보이는 것만을 선택하는 알고리즘. 매 순간 가장 좋아 보이는 것을 선택하며, 현재의 선택이 나중에 미칠 영향에 대해서는 고려하지 않는다.

탐욕적으로 문제에 접근했을 때 정확한 답을 찾을 수 있다는 보장이 있으면 매우 효과적이고 직관적인 알고리즘이지만, 대부분의 문제에 대해서는 "최적의 해"를 찾을 수 없는 가능성이 크기 때문에 주의해서 사용해야 하는 알고리즘입니다. 매 순간의 선택은 그 순간에 대해서는 최적이었을지라도 그것이 결론적으로 최적이 아닐 수 있기 때문입니다. 그렇기 때문에 그리디 알고리즘을 이용해 문제를 해법을 찾을 경우, 그 해법이 정당한지에 대해서 반드시 확인해 보아야 합니다.


1. 스택 생성
2. number를 순회->for num in number:
    1. 다음 조건문을 모두 만족할 경우 명령문 반복
    2. 조건문
        1. k>0
        2. 스택이 비어있지 않음
        3. 스택 마지막 값 < num
            명령문
                1.스택 pop
                2. k --
3. k>0이상이면 스택에서 k개 삭제 후 join해서 결과 값 반환

- 예시

number = "4177252841", k=4일 경우,

    (k=4) []
    (k=4) [4]
    (k=4) [4, 1]
    (k=3) [4]
    (k=2) []
    (k=2) [7]
    (k=2) [7, 7]
    (k=2) [7, 7, 2]
    (k=1) [7, 7]
    (k=1) [7, 7, 5]
    (k=1) [7, 7, 5, 2]
    (k=0) [7, 7, 5]
    (k=0) [7, 7, 5, 8]
    (k=0) [7, 7, 5, 8, 4]
    (k=0) [7, 7, 5, 8, 4, 1]
    retrun "775841"


```python
def solution(number, k):
    answer = [] # Stack
    
    for num in number:
        if not answer:
            answer.append(num)
            continue
        if k > 0:
            while answer[-1] < num:
                answer.pop()
                k -= 1
                if not answer or k <= 0:
                    break
        answer.append(num)
        
    answer = answer[:-k] if k > 0 else answer
    return ''.join(answer)
```


```python
solution("4177252841",4)
```




    '775841'




```python
def solution(number, k):
    answer = [] # Stack
    
    for num in number:
        while k > 0 and answer and answer[-1] < num:
            answer.pop()
            k -= 1
        answer.append(num)
        
    return ''.join(answer[:len(answer) - k])

```


```python
solution("4177252841",4)
```




    '775841'




```python
def solution(number, k):
    answer = [] # Stack
    
    for num in number:
        while k > 0 and answer and answer[-1] < num:
            answer.pop()
            k -= 1
        answer.append(num)
        
    return ''.join(answer[:len(answer) - k])
```


```python
solution("4177252841",4)
```




    '775841'




```python

```


```python

```
