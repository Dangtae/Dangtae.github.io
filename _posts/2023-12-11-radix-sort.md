---
layout: single
title:  "알고리즘 - 기수 정렬 알고리즘"
categories: Algorithm
tag: [알고리즘 공부, 정렬]
author_profile: false
sidebar: 
    nav: "counts"
---

## 기수 정렬 알고리즘

```python
from collections import deque

def radix_sort(A):
  queues = []
  for i in range(BUCKETS):
    queues.append(deque())

  n = len(A)
  factor = 1
  for d in range(DIGITS):
    for i in range(n):
      queues[A[i]//factor % BUCKETS].append(A[i])
    i = 0
    for b in range(BUCKETS):
      while queues[b]:
        A[i] = queues[b].popleft()
        i += 1
    factor *= BUCKETS
    print("step", d+1, A)
```

### 테스트 코드
```python
import random

BUCKETS = 10
DIGITS = 4

data = [random.randint(1,9999) for _ in range(10)]
radix_sort(data)
print("Radix:", data)
```

### 테스트 결과
```python
step 1 [910, 9701, 3293, 6294, 574, 6125, 9745, 5806, 8158, 4889]
step 2 [9701, 5806, 910, 6125, 9745, 8158, 574, 4889, 3293, 6294]
step 3 [6125, 8158, 3293, 6294, 574, 9701, 9745, 5806, 4889, 910]
step 4 [574, 910, 3293, 4889, 5806, 6125, 6294, 8158, 9701, 9745]
Radix: [574, 910, 3293, 4889, 5806, 6125, 6294, 8158, 9701, 9745]
```

### 기수 정렬의 특징
- 아무리 좋은 비교기반 정렬 알고리즘도 nlogn에 비례하는 시간 이상이 걸리지만 기수정렬은 O(dn)의 복잡도를 가짐
- 시간복잡도 측면에서 퀵 정렬이나 병합 정렬보다 훨씬 우월
- 정렬에 사용되는 킷값이 자연수로 표현되어야 적용가능, 리스트의 요소가 실수이거나 한글,한자면 적용 어려움
- 버킷을 위한 추가적인 메모리 필요
- 공간을 팔아서 시간을 버는 전략
