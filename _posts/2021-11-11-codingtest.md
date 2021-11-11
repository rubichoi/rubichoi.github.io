---
layout: single
title:  "핸드폰 번호 가리기"
---

핸드폰 번호 가리기

https://programmers.co.kr/learn/courses/30/lessons/12948

프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

제한 조건

s는 길이 4 이상, 20이하인 문자열입니다.

풀이)
폰 넘버의 길이를 세고, [-4:] 만큼은 그대로 두고 폰넘버 길이-4만큼 *을 붙여준다.


```python
def solution(phone_number):
    num = len(phone_number)
    four = phone_number[-4:]
    return "*"*(num-4)+four
```


```python
def hide_numbers(s):
    return "*"*(len(s)-4) + s[-4:]
```
