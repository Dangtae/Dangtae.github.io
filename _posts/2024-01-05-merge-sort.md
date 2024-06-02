---
layout: single
title:  "알고리즘 - 병합 정렬"
categories: Algorithm
tag: [알고리즘 공부, 분할 정복]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 병합 정렬

입력 리스트를 균등하게 두 부분으로 나누고, 각각을 정렬한 다음 결과를 병합합니다
이 과정은 부분 리스트의 크기가 1이 될 때까지 반복되는데, 크기가 1이면 그 부분 리스트는
이미 정렬된 것입니다

### 병합 정렬 알고리즘

```python
def merge_sort(A, left, right) :	    # A[left..right]를 오름차순으로 정렬
    if left<right :			            # 항목이 2개 이상인 경우
        mid = (left + right) // 2		# 리스트의 균등 분할
        merge_sort(A, left, mid)		# 부분 리스트 정렬
        merge_sort(A, mid + 1, right)	# 부분 리스트 정렬
        merge(A, left, mid, right)	# 병합
    # else: 항목이 1개 인 경우. 자동으로 정복되었음(하나이므로)
```

#### merge 함수
- A[i]와 A[j]를 비교하여 더 작은 요소를 임시 리스트 sorted에 복사하고 인덱스를 증가시킨다

```python
def merge(A, left, mid, right) :
    k = left			# 병합을 위한 임시 리스트의 인덱스
    i = left			# 왼쪽 리스트의 인덱스
    j = mid + 1			# 오른쪽 리스트의 인덱스
    while i<=mid and j<=right :
        if A[i] <= A[j] :	
            sorted[k] = A[i]
            i, k = i+1, k+1
        else:
            sorted[k] = A[j]
            j, k = j+1, k+1

    if i > mid :			# 한쪽에 남아 있는 레코드의 일괄 복사
        sorted[k:k+right-j+1] = A[j:right+1]	# 슬라이싱 이용
    else :
        sorted[k:k+mid-i+1] = A[i:mid+1]		# 슬라이싱 이용

    A[left:right+1] = sorted[left:right+1]		# A로 복사
```

### 병합 정렬은 얼마나 빠를까?
- merge_sort()에서 순환 호출의 깊이는 $log_{2}{n}$이다
- 병합(merge)단계에서 보면 임시 배열에 복사했다가 다시 가져와야하므로
총 부분 리스트에 들어 있는 요소의 개수가 n인 경우, 2n번의 이동이 발생
따라서 병합 단계에서 2n번의 이동 연산이 필요하다

- $log_{2}{n}$ x $2n$ 이므로 $O(nlog_{2}{n})$ 이다

### 병합 정렬의 특징
- 분할 정복의 대표적인 알고리즘으로 $O(nlog_{2}{n})$의 복잡도를 갖는
매우 효율적인 정렬 방법이다
- 입력의 구성과 상관없이 동일한 시간에 정렬되고, 안정성을 만족
- 제자리 정렬이 아님, 입력 리스트의 크기와 같은 크기의 입력 리스트가 반드시 있어야함
- 병합 정렬에서 부분 리스트를 두 개 이상으로 나누고 결과를 병합하는 다중(multiway) 병합 정렬이 있음, 
주 메모리보다 속도가 느린 보조 메모리에 있는 파일을 정렬하는 등의 응용에서 특히 유용하게 사용될 수 있음