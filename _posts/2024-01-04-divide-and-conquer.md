---
layout: single
title:  "알고리즘 - 분할 정복이란?"
categories: Algorithm
tag: [알고리즘 공부, 분할 정복]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 분할 정복이란?

- 주어진 문제를 둘 또는 여러 개의 작은 부분 문제들로 나누고, 이들을 각각 해결한 다음
결과를 모아서 원래의 문제를 해결하는 전략

### 문제 해결 단계
- 분할(divide): 주어진 문제를 같은 유형의 부분 문제들로 분할합니다
- 정복(conquer): 부분 문제들을 해결하여 결과(부분적인)를 만듭니다
- 병합(combine): 부분적인 결과들을 묶어 최종 결과를 만듭니다


분할 정복이 모든 문제에서 더 효율적인 것은 아닙니다. 그렇지만 정렬이나 탐색과 같은 많은
중요한 문제에서 상당한 효과를 발휘합니다

### 분할 정복과 축소 정복
- 축소 정복: 원래의 문제를 나눈 후에 해결해야 할 부분 문제가 하나만 남는 특별한 경우
- 정렬된 배열에서의 이진 탐색은 분할 정복 전략 중에서도 축소 정복을 이용하는 것

