---
layout: single
title:  "알고리즘 - 선택 정렬 알고리즘"
categories: CodingTest
tag: [알고리즘 공부, 정렬]
author_profile: false
sidebar: 
    nav: "counts"
---

## 선택 정렬 알고리즘 (제자리 정렬 방식)

```python
def selection_sort(A):
  n = len(A)
  for i in range(n-1):
    least = i
    for j in range(i+1, n):
      if A[j] < A[least]:
        least = j
    A[i], A[least] = A[least], A[i]
    print("Step %2d = "%(i+1), A)

##test
data = [6,3,7,4,9,1,5,2,8]
print("Original :", data)
selection_sort(data)
print("Selction :", data)

```

### 테스트 출력결과
```python
Original : [6, 3, 7, 4, 9, 1, 5, 2, 8]
Step  1 =  [1, 3, 7, 4, 9, 6, 5, 2, 8]
Step  2 =  [1, 2, 7, 4, 9, 6, 5, 3, 8]
Step  3 =  [1, 2, 3, 4, 9, 6, 5, 7, 8]
Step  4 =  [1, 2, 3, 4, 9, 6, 5, 7, 8]
Step  5 =  [1, 2, 3, 4, 5, 6, 9, 7, 8]
Step  6 =  [1, 2, 3, 4, 5, 6, 9, 7, 8]
Step  7 =  [1, 2, 3, 4, 5, 6, 7, 9, 8]
Step  8 =  [1, 2, 3, 4, 5, 6, 7, 8, 9]
Selction : [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

### 선택 정렬의 특징
- 시간 복잡도가 O(n^2)으로 효율적이지 않음
- 안정성 만족 x 
- 제자리 정렬로 추가적인 리스트 필요 x
- 알고리즘은 간단
- 자료의 구성에 상관없이 연산의 횟수가 결정되는 장점
- 리스트의 크기가 크지 않으면 충분히 사용가능한 알고리즘





