---
layout: single
title:  "알고리즘 - 억지 기법"
categories: Algorithm
tag: [알고리즘 공부, 알고리즘 설계 전략]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 억지 기법

- 해결하지 못하는 것보다 단순하게라도 해결하는 것이 훨씬 좋다
- 쉬운 문제를 어렵게 풀 필요는 없다
- 매우 광범위한 문제에 적용가능
- 입력의 크기가 작을 경우 충분히 빠를 수 있고, 점근적으로 더 효율적인
알고리즘보다 실제로는 더 빠를 수도 있다
- 더 효율적인 알고리즘의 설계와 분석을 위한 이론적인 기반

### 문자열 매칭 문제
- 텍스트의 첫 번째 문자 위치에 패턴을 놓고 한 문자씩 비교합니다. 서로 다른 문자가 나오면 패턴을
다음 위치로 옮겨 다시 앞의 과정을 반복하는데, 성공한 매칭이 나타날 때까지 반복합니다

```python
def string_matching(T, P):   # T: 입력 문자열(텍스트) , P: 탐색 패턴
    n = len(T)               # n: 텍스트의 길이
    m = len(P)               # m: 패턴의 길이

    for i in range(n-m+1):
        j = 0
        while j < m and P[j] == T[i+j]:
            j = j + 1
        if j == m:
            return i        # 매칭 성공
    return -1               # 매칭 실패
```
#### 복잡도 분석
- 최선의 경우: 텍스트 T의 맨 앞의 문자열이 패턴 P와 일치할 때, 시간복잡도 $O(m)$
- 최악의 경우: n-m+1번 시작 위치가 달라지고 각 위치에서도 패턴의 모든 문자를 비교하는 경우, 시간복잡도 $O(nm)$


### 배낭 채우기 문제(Knapsack problem)
- n개의 물건의 집합에 대한 모든 부분집합을 만들고, 무게 합이 배낭 용량을 넘지 않으면서 가치가 최대인 것 찾기

```python
def Knapsack01_BF(wgt, val, W):
    n = len(wgt)        # 전체 물건의 수
    bestVal = 0         # 배낭의 최대 가치

    for i in range(2 ** n):
        s = [0] * n
        for d in range(n):
            s[d] = i % 2
            i = i // 2

        sumVal = 0
        sumWgt - 0
        for d in range(n):
            if s[d] == 1:
                sumWgt += wgt[d]
                sumVal += val[d]
        if sumWgt <= W:
            if sumVal > bestVal:
                bestVal = sumVal
    return bestVal      # 최대 가치 반환

```

#### 복잡도 분석
- 알고리즘의 복잡도 : $O(2^n)$

억지기법 알고리즘 방법은 항상 최적의 해를 구해주지만, 역시 복잡도가 너무 높아
n이 조금만 커져도 현실적으로 사용하기 어렵다는 한계가 있음