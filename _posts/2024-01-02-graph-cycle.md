---
layout: single
title:  "알고리즘 - 그래프 순회"
categories: Algorithm
tag: [알고리즘 공부, 그래프]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 그래프 순회

### 깊이 우선 탐색(DFS: Depth First Search)

- 시작 정점에서 한 방향으로 계속 가다가 더 이상 갈 수 없으면 가장 가까운
갈림길로 다시 돌아와 다른 방향을 다시 탐색, 이진 트리의 전위 순회와 비슷

#### 깊이 우선 탐색(인접행렬 방식)

```python
def DFS(vtx, adj, s, visited):
    print(vtx[s], end = ' ')
    visited[s] - True

    for v in range(len(vtx)):
        if adj[s][v] != 0:
            if visited[v] == False:
                DFS(vtx, adj, v, visited)
```

#### 깊이 우선 탐색 테스트 프로그램

```python
vtx = ['U', 'V', 'W', 'X', 'Y']
edge = [[0, 1, 1, 0, 0], ...]

print('DFS(출발:U) : ', end="")
DFS(vtx, edge, 0 , [FALSE]*len(vtx))
print()
```
##### 실행 결과
```python
DFS(출발: U): U V W Y X
```

### 너비 우선 탐색

- 시작 정점에서 가까운 정점을 먼저 방문하고 먼 정점을 나중에 방문, 이진 트리의 레벨순회와 비슷

#### 너비 우선 탐색(인접 리스트 방식)

```python
from queue import Queue
def BFS_AL(vtx, aList, s):
    n = len(vtx)
    visited = [False] * n
    Q = Queue()
    Q.put(s)
    visited[s] = True
    while not Q.empty():
        s = Q.get()
        print(vtx[s], end = ' ')
        for v in aList[s]:
            if visited[v] == False:
                Q.put(v)
                visited[v] = True
```

#### 너비 우선 탐색 테스트 프로그램

```python
vtx = ['U', 'V', 'W', 'X', 'Y']
aList = [[1,2], ...]
print('BFS_AL(출발:U): ', end = "")
BFS_AL(vtx, aList, 0)
print()
```

##### 실행 결과
```python
BFS_AL(출발: U): U V W X Y
```