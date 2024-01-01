---
layout: single
title:  "알고리즘 - 순차 탐색 알고리즘"
categories: Algorithm
tag: [알고리즘 공부, 탐색]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 순차 탐색 알고리즘

```python
def sequential_search(A, key, low, high):
    for i in range(low, high + 1):  # i: low, low + 1, ...high
        if A[i] == key:             # 탐색 성공하면
            return i                # 인덱스 반환
    return -1                       # 탐색에 실패하면 -1 반환
```

### 순차 탐색의 특징
- 탐색의 정의를 직접 사용하는 알고리즘으로 간단하고 구현하기 쉽다
- 효율적이지는 않다. 탐색 성능은 최선의 경우 $O(1)$이고 최악이나
평균적인 경우가 $O(n)$ 인데, 최선의 경우는 큰 의미가 없다
- 테이블이 정렬되어 있지 않다면 순차 탐색 이외에 별다른 대안은 없다

### 순차 탐색을 개선하는 방법?

#### 자기 구성 순차 탐색
- 탐색이 진행될 때마다 자주 사용되는 레코드를 앞쪽으로 옮기는 방법
- 리스트를 재구성하여 탐색의 효율을 끌어올리려는 것

##### 맨 앞으로 보내기 (move to front)
- 탐색에 성공한 레코드를 리스트의 맨 앞으로 보내는 방법
- 리스트의 맨앞으로 보내면서 모든 레코드들이 뒤로 한칸씩 밀림
- 연결 구조에선 훨씬 효율적으로 처리 가능 $O(1)$
- 한번 탐색된 레코드가 바로 이어서 다시 탐색될 가능성이 많은 응용에만 사용해야 함

##### 교환하기 (transpose)
- 탐색되면 위치를 바로 앞의 레코드와 교환
- 자주 탐색되는 레코드는 점진적으로 앞으로 이동

```python
def sequential_search_transpose(A, key, low , high):
    for i in range(low, high + 1):
        if A[i] == key:
            if i > low:                # 맨 처음 요소가 아니면
                A[i] , A[i-1] = A[i-1], A[i] # 교환하기 (transpose)
                i = i -1               # 한 칸 앞으로 왔음
            return i                   # 탐색에 성공하면 키 값의 인덱스 반환
    return -1                          # 탐색에 실패하면 -1 반환
```
