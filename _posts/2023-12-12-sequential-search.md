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
  for i in range(low, high + 1):
    if A[i] == key:
      return i
  return -1
```

### 순차 탐색의 특징
- 간단하고 구현하기 쉬움
- 효율적이진 않음, 탐색성능은 최선 $O(1)$ 최악 또는 평균 $O(n)$
- 테이블이 정렬되어 있지 않다면 순차 탐색 이외에 별다른 대안은 없다
