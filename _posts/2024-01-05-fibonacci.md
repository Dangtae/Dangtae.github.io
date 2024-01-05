---
layout: single
title:  "알고리즘 - 피보나치 수열과 분할 정복의 주의점"
categories: Algorithm
tag: [알고리즘 공부, 분할 정복]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 피보나치 수열과 분할 정복의 주의점

### 분할 정복을 이용한 피보나치 수열

```python
def fib(n) :
#    if n==3 : print("fib(3)")

    if n == 0 : return 0		# 정복: 0번째 달
    elif n == 1 : return 1	    # 정복: 1번째 달
    else : 
        return fib(n-1) + fib(n-2)		# 분할과 병합
```

- 문제를 나눌때마다 해결해야 할 전체 부분 문제의 크기가 거의 두배로 늘어남
- 알고리즘의 시간복잡도 $O(2^n)$으로 매우 비효율적

### 피보나치 수열의 다른 알고리즘들

```python
def fib_mat(n) :
    if n == 0 : return 0        # 정복: 0번째 달
    elif n == 1 : return 1      # 정복: 1번째 달

    mat = [[1,1],[1,0]]         # 초기 피보나치 행렬
    result = powerMat(mat, n)   # 축소정복 방식
    return result[0][1]         # fib(n) 부분을 반환
```

- 행렬 거듭제곱 전략을 이용하면 $O(log_{2}{n})$에 계산이 완료
- 가장 빠른 피보나치 수열 알고리즘