---
layout: single
title:  "프로그래머스 전화번호목록 파이썬"
---

전화번호목록

https://programmers.co.kr/learn/courses/30/lessons/42577


```python
def solution(phoneBook):
    # 1. 비교할 A선택 
    for i in range(len(phoneBook)):
        # 2. 비교할 B선택 
        for j in range(i+1, len(phoneBook)):
            # 3. 서로가 서로의 접두어인지 확인한다. 
            if phoneBook[i].startswith(phoneBook[j]):
                return False 
            if phoneBook[j].startswith(phoneBook[i]):
                return False 
    return True 

print(solution(["6", "12", "6789"]))
```

    False
    


```python
def solution(phone_book):
    # 1. Hash map을 만든다 
    hash_map = {} 
    for phone_number in phone_book:
        hash_map[phone_number] = 1
        
        
    # 2. 접두어가 Hash map에 존재하는지 찾는다 
    for phone_number in phone_book: 
        jubdoo = "" 
        for number in phone_number: 
            jubdoo += number 
            # 3. 접두어를 찾아야 한다 (기존 번호와 같은 경우 제외)
            if jubdoo in hash_map and jubdoo != phone_number: 
                return False 
    return True 
print(solution(["6", "12", "6789"]))
```

    False
    
