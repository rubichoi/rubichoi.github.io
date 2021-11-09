

스택/큐 - 주식가격

- 몇초동안 가격이 안떨어지고 있는지 리턴하기.


- 파이썬은 answer = [0] * 개수 하면 개수만큼 0으로 초기화된 리스트가 만들어 진다.


```python
def solution(prices):
    answer =[0] * len(prices)
    for i in range(len(prices)):
        for j in range(i+1, len(prices)):
            if prices[i] <= prices[j]:
                answer[i]+=1
            else:
                answer[i]+=1
                break
    return answer
```


```python
prices = [1, 2, 3, 2, 3]
```


```python
solution(prices)
```




    [4, 3, 1, 1, 0]



- 스택으로 푸는 방법은 처음 price를 stack에 쌓고 다음 price가 더 크면 스택에 쌓고 작으면 pop을 한다. 


```python
def solution(prices):
    answer = [0]*len(prices)
    stack = []
 
    for i, price in enumerate(prices):
        #stack이 비었이면 false
        while stack and price < prices[stack[-1]]:
            j = stack.pop()
            answer[j] = i - j
        stack.append(i)
 
    # for문 다 돌고 Stack에 남아있는 값들 pop
    while stack:
        j = stack.pop()
        answer[j] = len(prices) - 1 - j
 
    return answer
```


```python
solution(prices)
```




    [4, 3, 1, 1, 0]


