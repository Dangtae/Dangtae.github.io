---
layout: single
title:  "알고리즘 - 백트래킹"
categories: Algorithm
tag: [알고리즘 공부, 공간으로 시간벌기와 백트래킹]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 백트래킹

- 미로를 탐색하다가 길이 갈라지는 분기점을 만나면, 일단 하나를 선택해 탐색을 계속하고, 그 길이
막히면 다시 분기점으로 되돌아와(backtracking) 시도하지 않았던 다른 길을 탐색

### 틱택토 게임과 상태 공간 트리
- 틱택토 게임: 같은 글자가 가로, 세로, 혹은 대각선 상에 놓이면 이기는 게임
- 상태공간트리: 틱택토 문제에 대한 모든 상태를 트리 구조로 나타내고 있는 트리
- 상태공간트리는 어떤 문제에 대한 모든 상태를 노드로 포함하고 있음
- 상태공간트리에서 해를 찾는 가장 직접적인 방법은 완전 탐색(exhaustive search)

### 백트래킹이란?
- 상태공간트리를 보다 효율적으로 탐색하는 방법 제공
- 기본 골격은 깊이우선탐색(DFS)
- 상태공간트리를 루트에서부터 깊이우선으로 탐색해 내려오다가 단말 노드까지 가기 전에
방문한 노드(후보해)가 요구하는 해가 아니라고 판단되면 더는 탐색하지 않고 이전 노드로
되돌아 나오는(backtracking) 전략을 사용

=> 상태공간트리의 많은 노드들을 탐색하지 않고 미리 가지치기(pruning)할 수 있고, 따라서 탐색의 효율을 높일 수 있다

### N-Queen 문제
- N X N 의 체스보드에 N개의 퀸을 놓는 문제인데, 어떤 퀸도 다른 퀸을 공격할 수 없어야 함
- 가장 단순한 방법은 $N^2$개의 모든 칸 중에서 임의로 N개를 골라 퀸을 배치하고 서로 공격하는 퀸이 있는지를 검사

### 백트래킹 전략
-  첫 행 부터 순서대로 퀸을 배치하는데, 불가능한 위치에 퀸을 놓고 더 탐색하는 것이 아니라
백트래킹 한다

### N-Queen 알고리즘
- 먼저 현재의 보드 상태에서 (x,y)칸에 퀸을 놓을 수 있는지를 판단하는 함수 필요

```python
def isSafe(board, x, y):
    N = len(board)

    for i in range(y):      
        if board[i][x] == 1: return False   # 세로방향 검사
    for i, j in zip(range(y-1, -1, -1), range(x-1, -1, -1)):
        if board[i][j] == 1: return False   # \ 방향 검사
    for i, j in zip(range(y-1, -1, -1), range(x+1, N)):
        if board[i][j] == 1: return False   # / 방향 검사
    return True     # 모든 방향으로 OK이면 (x,y)는 safe한 위치
```
- 순환을 이용해 N-Queen 알고리즘 기술
- 0~y-1행까지는 퀸이 놓인 상태에서 y행부터 모든 행에 새로운 퀸을 놓는 알고리즘

```python
def solve_N_Queen(board, y):
    N = len(board)
    if y == N:                      # 하나의 해 탐색 성공
        printBoard(board)           # 화면에 출력
        return                      # 백트래킹

    for x in range(N):           	# 현재 y에서 모든 x를 테스트 함
        if isSafe(board, x, y):   	# (x,y)에 퀸이 들어갈 수 있으면
            board[y][x] = 1        	# 넣고
            solve_N_Queen(board, y+1)# 다음 행 처리: 상태공간트리 탐색
            board[y][x] = 0			# 처리가 끝났으니 다시 꺼냄

```
#### 테스트 프로그램
```python
def printBoard(board):
    for i in range(len(board)):
        for j in range(len(board)):
            if board[i][j] == 1:
                print("Q", end=" ")
            else:
                print(".", end=" ")
        print()
    print()

```

```python
N = 4
board = [[0 for i in range(N)] for j in range(N)]
solve_N_Queen(board, 0)
```
#### 실행결과
```python
. Q . . 
. . . Q 
Q . . . 
. . Q .

. . Q .
Q . . .
. . . Q
. Q . .
```


