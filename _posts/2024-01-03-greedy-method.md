---
layout: single
title:  "알고리즘 - 탐욕적 기법"
categories: Algorithm
tag: [알고리즘 공부, 알고리즘 설계 전략]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 탐욕적 기법

- '그 순간에 최적' 이라고 생각되는 답을 선택

### 거스름돈 동전 최소화
- 액면가가 가장 높은 동전부터 탐욕적으로 최대한 사용하면서 거스름돈을 맞춘다

#### 최적해를 구할까?
- 동전의 액면가 중에서 어떤 두 개를 고르더라도 큰 액면가를 작은 액면가로 나누어 떨어지는
동전 체계를 갖는다면 최적해를 보장


### 분할 가능한 배낭 채우기
- 0-1 배낭 문제는 탐욕적 기법으로 최적해 구하지 못함

만약 물건들이 가루로 되어 있어 일부분만을 배낭에 넣을 수 있다면?

```python
def KnapSackFrac(wgt, val, W):
    bestval = 0            # 최대 가치
    for i in range(len(wgt)):
        if W <= 0 :
            break
        if W >= wgt[i]:
            W -= wgt[i]
            bestVal += val[i]
        else:
            fraction = W / wgt[i]
            bestVal += val[i] * fraction
            break
    return bestVal        # 최대 가치 반환

```

#### 최적 해를 보장할까?
- 넣을 수 있는 모든 공간을 항상 무게당 가격이 가장 높은 것부터 채우기 때문에
최적해를 확실히 보장한다
- 알고리즘의 복잡도는 $O(n)$ 이다