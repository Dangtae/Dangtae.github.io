---
layout: single
title:  "알고리즘 - 신장 트리"
categories: Algorithm
tag: [알고리즘 공부, 그래프]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 신장 트리

- 그래프 내 모든 정점을 포함하는 트리
- 그래프 정점 수가 n이라면 신장 트리는 정확히 n-1개의 간선으로 모든 정점을 연결해야 함
- 깊이 우선이나 너비 우선 탐색 도중에 사용된 간선들만 모으면 신장 트리가 만들어짐

### DFS를 이용한 신장트리 (인접행렬 방식)

```python
def ST_DFS(vtx, adj, s, visited):
    visited[s] = True
    for v in range(len(vtx)):
        if adj[s][v] != 0:
            if visited[v] == False:
                print("(", vtx[s], vtx[v], ")", end= ' ')
                ST_DFS(vtx, adj, v, visited)
```

#### 실행 결과
```python
ST_DFS_AM: ( U V ) ( V W ) ( W Y ) ( V X )
```
