---
layout: single
title:  "알고리즘 - 이진 탐색 트리"
categories: Algorithm
tag: [알고리즘 공부, 탐색]
author_profile: false
sidebar: 
    nav: "counts"
use_math: true
---

## 이진 탐색 트리

- 탐색의 성능은 유지하면서 '삽입'과 '삭제'도 효율적으로 처리하려고 하는 것

### 이진 탐색 트리를 위한 노드 클래스
```python
class BSTNode:
    def __init__ (self, key, value):
        self.key = key 
        self.value = value
        self.left = None
        self.right = None

```

### 탐색 알고리즘: 키를 이용한 탐색

#### 이진 탐색 트리의 탐색 연산(순환 구조)
```python
def search_bst(n, key):
    if n == None:
        return None
    elif key == n.key:
        retun n
    elif key < n.key:
        return search_bst(n.left, key)
    else:
        return search_bst(n.right, key)
```

### 탐색 알고리즘: 값을 이용한 탐색
#### 이진 탐색 트리의 값을 이용한 탐색(전위 순회)
```python
def search_value_bst(n, value):
    if n == None:
        return None
    elif value == n.value:
        return n
    res = search_value_bst(n.left, value)
    if res i not None:
        return res
    else:
        return search_value_bst(n.right, value)
```

## 이진 탐색 트리의 삽입 연산
```python
def insert_bst(root, node):
    if root == None:           # 공백 노드에 도달하면, 이 위치에 삽입
        return node            # node를 반환(이 노드가 현재 root 위치에 감)
    
    if node.key == root.key:   # 동일한 키는 허용하지 않음
        return root            # root를 반환(root는 변화 없음)
    
    if node.key < root.key:
        root.left = insert_bst(root.left, node)
    else:
        root.right = insert_bst(root.right, node)

    return root                # root를 반환(root는 변화 없음)
```
## 이진 탐색 트리의 삭제 연산
- Case 1: 단말 노드의 삭제
- Case 2: 자식이 하나인 노드의 삭제
- Case 3: 2개의 자식을 모두 갖는 노드의 삭제

```python
def delete_bst(root, key):
    if root =- None:   # 공백 트리
        return root

    if key < root.key:
        root.left = delete_bst(root.left, key)
    elif key > root.key:
        root.right = delet_bst(root.right, key)
    
    # key가 루트의 키와 같으면 root를 삭제
    else:
        # case1(단말 노드) 또는 case2(오른쪽 자식만 있는 경우)
        if root.left == None:
            return root.right
        
        # case2(왼쪽 자식만 있는 경우)
        if root.right == None:
            return root.left
        
        # case3(두 자식만 모두 있는 경우)
        succ = root.right
        while succ.left != None:
            succ = succ.left
        root.key = succ.key
        root.value = succ.value
        root.right = delete_bst(root.right, succ.key)

    return root
```

## 이진 탐색 트리의 성능
- 최선의 경우는 포화 이진 트리일 때, 탐색과 삽입, 삭제 연산이 $O(\log_{2}{(n)})$에 처리
- 이진 탐색과 탐색 성능은 같지만, 삽입과 삭제 연산이 훨씬 효율적
- 한쪽으로 치우치는 경사 트리인 경우 트리의 높이 h는 n과 같아진다.
순차 탐색과 같이 n에 비례하는, 즉 $O(n)$이 되는 매우 비효율적인 상황