---
layout: single
title:  "알고리즘 - 이진 탐색 알고리즘"
categories: Algorithm
tag: [알고리즘 공부, 탐색]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 이진 탐색 알고리즘


### 순환 구조

```python
def binary_search(A, key, low, high):
  if (low <= high):
    middle = (low + high) // 2
    if key == A[middle]:
      return middle
    elif key < A[middle]:
      return binary_search(A, key, low, middle - 1)
    else:
      return binary_search(A, key, middle + 1, high)
  return -1
```

### 반복 구조

```python
def binary_search_iter(A, key, low, high):
  while low <= high:
    middle = (low + high) // 2
    if key == A[middle]:
      return middle
    elif key < A[middle]:
      high = middle -1
    else:
      low = middle + 1
  return -1
```

### 이진 탐색의 특징

- $\log_{2}{(n)}$의 매우 효율적인 탐색 방법
- 반드시 배열이 정렬되어 있어야 사용가능 
- 테이블이 한번 만들어지면 이후로 변경되지 않고 탐색 연산만 처리한다면 이진 탐색이 최고의 선택 중 하나이다