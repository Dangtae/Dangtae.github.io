---
layout: single
title:  "알고리즘 - 삽입 정렬 알고리즘"
categories: CodingTest
tag: [알고리즘 공부, 정렬]
author_profile: false
sidebar: 
    nav: "counts"
---

## 삽입 정렬 알고리즘

```python
def insertion_sort(A):
  n = len(A)
  for i in range(1, n):
    key = A[i]
    j = i - 1
    while j >= 0 and A[j] > key:
      A[j + 1] = A[j]
      j -= 1
    A[j+1] = key
    print("Stage %2d ="%i, A)

##test
data = [6,3,7,4,9,1,5,2,8]
print("Original =", data)
insertion_sort(data)
print("inserted =", data)
```

### 테스트 결과
```python
Original = [6, 3, 7, 4, 9, 1, 5, 2, 8]
Stage  1 = [3, 6, 7, 4, 9, 1, 5, 2, 8]
Stage  2 = [3, 6, 7, 4, 9, 1, 5, 2, 8]
Stage  3 = [3, 4, 6, 7, 9, 1, 5, 2, 8]
Stage  4 = [3, 4, 6, 7, 9, 1, 5, 2, 8]
Stage  5 = [1, 3, 4, 6, 7, 9, 5, 2, 8]
Stage  6 = [1, 3, 4, 5, 6, 7, 9, 2, 8]
Stage  7 = [1, 2, 3, 4, 5, 6, 7, 9, 8]
Stage  8 = [1, 2, 3, 4, 5, 6, 7, 8, 9]
inserted = [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 삽입 정렬의 특징
- 시간 복잡도가 O(n^2)으로 효율적이지 않은 알고리즘
- 끼워넣기를 위해 많은 레코드의 이동이 필요하므로 레코드의 크기가 큰 경우 선택 정렬보다도 효율적이지 않음
- 제자리 정렬, 안정성 충족
- 레코드 대부분이 정렬된 경우라면 효율적으로 사용가능