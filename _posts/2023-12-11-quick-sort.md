---
layout: single
title:  "알고리즘 - 퀵 정렬 알고리즘"
categories: Algorithm
tag: [알고리즘 공부, 정렬]
author_profile: false
sidebar: 
    nav: "counts"
---

## 퀵 정렬 알고리즘

```python
def partition(A, left, right):
  pivot = A[left]
  low = left + 1
  high = right
  while (low < high): #low와 high 가 역전되지 않는 한 반복
    while low <= right and A[low] <= pivot:
      low += 1   #A[low]<=피벗이면 low를 오른쪽으로 진행

    while high >= left and A[high] >= pivot:
      high -= 1  #A[high] >=피벗이면 high를 왼쪽으로 진행

    if low < high: # 역전이 아니면 두 레코드 변환
      A[low], A[high] = A[high], A[low]
  A[left], A[high] = A[high], A[left]
  return high


def quick_sort(A, left, right):
  if left < right: #정렬 범위가 2개 이상인 경우, 하나 이하면 이미 정렬된 것
    q = partition(A, left, right)
    quick_sort(A, left, q - 1)
    quick_sort(A, q + 1, right)
```

### 테스트 코드
```python
data = [5,3,8,4,9,1,6,2,7]
quick_sort(data, 0, len(data)-1)
```
### 테스트 결과
```python
Original : [5,3,8,4,9,1,6,2,7]
QuickSort : [1,2,3,4,5,6,7,8,9]
```

### 퀵 정렬의 특징
- 평균적으로는 최선의 입력과 비슷한 속도
- 불필요한 데이터의 이동 줄이고 먼 거리의 데이터를 교환, 한번 결정된 피벗들이 추후 연산에서 제외