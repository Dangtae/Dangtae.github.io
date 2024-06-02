---
layout: single
title:  "알고리즘 - 보간 탐색 알고리즘"
categories: Algorithm
tag: [알고리즘 공부, 탐색]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 보간 탐색 알고리즘

```python
def binary_search_iter(A, key, low, high):
  while low <= high:
    middle = int(low + (high-low) * (key - A[low].key) / (A[high].key-A[low].key))
    # 이진 탐색 함수에서 middle 계산만 다음과 같이 수정
    if key == A[middle]:
      return middle
    elif key < A[middle]:
      high = middle -1
    else:
      low = middle + 1
  return -1
```

### 보간 탐색의 특징
- 탐색 키가 존재할 위치를 예측하여 탐색하는 방법
- 이진탐색과 같은 시간복잡도를 갖지만 많은 데이터가 비교적 균등하게 분포된 자료의 경우
훨씬 효율적으로 사용될 수 있음