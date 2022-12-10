---
title: "[Algorithm] Graph Theory"
categories:
  - Algorithm
tags:
  - [algorithm, graph]

toc: true
toc_sticky: true
toc_label: "Content"
toc_icon: "sticky-note"
---

📣<br>
본 포스트는 '이것이 취업을 위한 코딩 테스트다 with 파이썬'을 공부하고 작성하였습니다 :)    
click > [(이코테 2021) 이것이 취업을 위한 코딩 테스트다 with 파이썬](https://www.youtube.com/watch?v=m-9pAwq1o3w)
{: .notice--primary}

# Graph Theory

## 이론

앞서 배운 DFS/BFS와 최단 경로에서 다룬 내용들 모두 그래프 알고리즘의 한 유형이다. 그 외에도 다양한 그래프 알고리즘이 있는데, 이 장에서는 그 중에서 몇 가지를 추가적으로 배운다. 

### 서로소 집합 (Disjoint Sets)

공통 원소가 없는 두 집합을 의미한다. 

**서로소 집합 자료구조** 

서로소 부분 집합들로 나누어진 원소들의 데이터를 처리하기 위한 자료구조로 union과 find 2개의 연산으로 조작할 수 있다. 집합은 트리 자료구조를 이용하여 표현한다. 

- **union 연산** : 2개의 원소가 포함된 집합을 하나의 집합으로 합치는 연산이다.
- **find 연산** : 특정한 원소가 속한 집합이 어떤 집합인지 알려주는 연산이다.

**서로소 집합 계산 알고리즘**

1. union 연산을 확인하며, 서로 연결된 두 노드 A, B를 확인한다. 
    1. A와 B의 루트 노드를 각각 찾는다. 
    2. A의 루트 노드를 B의 루트 노드로 설정한다. (더 작은 루트 노드를 가리키도록 한다. )
2. 모든 union 연산을 처리할 때까지 1의 과정을 반복한다. 

**서로소 집합 알고리즘 소스코드**

```python
# 특정 원소가 속한 집합을 찾기
def find_parent(parent, x):
	# 루트 노드가 아니라면, 루트 노드를 찾을 때까지 재귀적으로 호출
	if parent[x] != x:
		parent[x] = find_parent(parent, parent[x])
	return parent[x]

# 두 원소가 속한 집합을 합치기
def union_parent(parent, a, b):
	a = find_parent(parent, a)
	b = find_parent(parent, a)
	if a < b:
		parent[b] = a
	else : 
		parent[a] = b

# 노드의 개수와 간선(union 연산)의 개수 입력받기
v, e = map(int, input(),split())
parent = [0] * (v+1) # 부모 테이블 초기화

# 부모 테이블상에서, 부모를 자기 자신으로 초기화
for i in range(1, v+1):
	parent[i] = i

# union 연산을 각각 수행
for i in range(e):
	a,b = map(int, input().split())
	union_parent(parent, a, b)

# 각 원소가 속한 집합 출력
print("각 원소가 속한 집합 : ", end="")
for i in range(1, v+1):
	print(find_parent(parent, i), end=" ")

print()

# 부모 테이블 내용 출력
print("부모 테이블: " end="")
for i in range(1, v+1):
	print(parent[i], end=" ")
```

**서로소 집합 알고리즘의 시간 복잡도**

노드의 개수가 V개고 최대 V-1 개의 union 연산과 M개의 find연산이 가능할 때 경로 압축 방법을 적용한 시간 복잡도는 $O(V + M(1 + M(1 + log_{1-M/V}V))$ 이다. 

**서로소 집합을 활용한 사이클 판별**

서로소 집합은 다양한 알고리즘에 사용할 수 있는데, 특히 서로소 집합은 무방향 그래프 내에서의 사이클을 판별할 때 사용할 수 있다. (방향 그래프에서의 사이클 여부는 DFS로 판별)

1. 각 간선을 확인하며 연결된 두 노드의 루트 노드를 확인한다. 
    1. 루트 노드가 서로 다르다면 두 노드에 대하여 union 연산을 수행한다. 
    2. 루트 노드가 서로 같다면 사이클이 발생한 것이다. 
2. 그래프에 포함되어 있는 모든 간선에 대하여 1번 과정을 반복한다. 

### 신장 트리

신장 트리 (Spanning Tree)란 하나의 그래프가 있을 때, 모든 노드를 포함하면서 사이클이 존재하지 않는 부분 그래프를 의미한다. 이 때, 모든 노드가 포함되어 서로 연결되면서 사이클이 존재하지 않는다는 조건은 트리의 성립 조건이기도 하다. 

![image](https://user-images.githubusercontent.com/68420044/206849877-5f6f4223-3a71-4f45-b58b-63aba25cfb0b.png)

 

**크루스칼 알고리즘**

신장 트리 중에서 최소 비용으로 만들 수 있는 신장 트리를 찾는 알고리즘을 ‘최소 신장 트리 알고리즘’이라고 한다. 대표적인 신장 트리 알고리즘으로 크루스칼 알고리즘이 있다. 

크루스칼 알고리즘을 사용하면 가장 적인 비용으로 모든 노드를 연결할 수 있다. 

1. 간선 데이터를 비용에 따라 오름차순으로 정렬한다. 
2. 간선을 하나씩 확인하며 현재의 간선이 사이클을 발생시키는지 확인한다. 
    1. 사이클이 발생하지 않는 경우, 최소 신장 트리에 포함시킨다. 
    2. 사이클을 발생하는 경우, 최소 신장 트리에 포함시키지 않는다. 
3. 모든 간선에 대하여 2번 과정을 반복한다. 

**크루스칼 알고리즘 소스코드**

```python
def find_parent(parent, x):
    if parent[x] != x:
        parent[x] = find_parent(parent, parent[x])
    return parent[x]

def union_parent(parent, a, b):
    a = find_parent(parent,a)
    b = find_parent(parent,b)
    if a<b:
        parent[b] = a
    else:
        parent[a] = b

v, e = map(int,input().split())
edges = [list(map(int, input().split())) for _ in range(e)]
parent = [i for i in range(v+1)]

edges.sort(key=lambda x:x[2])

result = 0
for edge in edges:
    a,b,cost = edge
    if find_parent(parent,a) != find_parent(parent,b):
        union_parent(parent,a,b)
        result+=cost

print(result)
```

**크루스칼 알고리즘의 시간복잡도**

크루스칼 알고리즘은 간선의 개수가 E일 때,  O(ElogE)의 시간 복잡도를 가진다. 

### 위상정렬 알고리즘

위상 정렬 (Topology Sort)는 정렬 알고리즘의 일종으로, 순서가 정해져 있는 이련의 작업을 순서대로 수행해야 할 떄 사용할 수 있는 알고리즘이다. 즉, 방향 그래프의 모든 노드를 방향성에 거스르지 않도록 순서대로 나열하는 것이다. 

진입차수(indegree) : 특정한 노드로 들어오는 간선의 개수이다. 

1. 진입차수가 0인 노드를 큐에 넣는다.
2. 큐가 빌 때까지 다음의 과정을 반복한다. 
    1. 큐에서 원소를 꺼내 해당 노드에서 출발하는 간선을 그래프에서 제거한다. 
    2. 새롭게 진입차수가 0이된 노드를 큐에 넣는다. 

```python
v, e = map(int, input().split())
indegree = [0] * (v + 1)
graph = [[] for i in range(v + 1)]
answer = [1] * (v + 1)

for _ in range(e):
    a, b = map(int, input().split())
    graph[a].append(b)
    indegree[b] += 1

def topology_sort():
		result = []
    q = deque()

    for i in range(1, v + 1):
        if indegree[i] == 0:
            q.append(i)

    while q:
        now = q.popleft()
        result.append(now)
        for i in graph[now]:
            indegree[i] -= 1
            if indegree[i] == 0:
                q.append(i)

topology_sort()
for i in result():
		print(i, end='')
```

**위상정렬의 시간 복잡도**

차례대로 모든 노드를 확인하면서, 해당 노드에서 출발하는 간선을 차례대로 제거해야 한다. 따라서 위상 정렬의 시간 복잡도는 O(V + E)이다. 

## 기출 **문제**


### [[Baekjoon 1647] 도시분할계획](https://www.acmicpc.net/problem/1238)

```python
import sys
input = sys.stdin.readline

# 특정 원소가 속한 집합을 찾기
def find_parent(parent, x):
    if parent[x] != x: # 루트 노드를 찾을 때까지
        parent[x] = find_parent(parent, parent[x])
    return parent[x]

# 두 원소가 속한 집합을 합치기
def union_parent(parent, a, b):
    a = find_parent(parent,a)
    b = find_parent(parent,b)
    if a<b:
        parent[b] = a
    else:
        parent[a] = b

v, e = map(int, input().split())
parent = [0] * (v+1)

# 모든 간선을 담을 리스트와 최종 비용을 담을 변수
edges = []
result = 0

for i in range(1, v+1):
    parent[i] = i
for _ in range(e):
    a,b, cost = map(int,input().split())
    edges.append((cost,a,b))

edges.sort() # 비용 순으로 정렬
max_edge = 0 # 최소 신장 트리에 포함되는 간선 중에서 가장 비용이 큰 간선

for edge in edges:
    cost,a,b = edge
    # 사이클이 발생하지 않는 경우
    if find_parent(parent,a) != find_parent(parent,b):
        union_parent(parent,a,b)
        result += cost
        max_edge = cost

print(result - max_edge)
```

### [[Baekjoon 14567] 선수과목](https://www.acmicpc.net/problem/14567)

```python
from collections import deque
import sys

input = sys.stdin.readline

v, e = map(int, input().split())
indegree = [0] * (v + 1)
graph = [[] for i in range(v + 1)]
answer = [1] * (v + 1)

for _ in range(e):
    a, b = map(int, input().split())
    graph[a].append(b)
    indegree[b] += 1

def topology_sort():
    q = deque()

    for i in range(1, v + 1):
        if indegree[i] == 0:
            q.append(i)

    while q:
        now = q.popleft()
        flag = False
        for i in graph[now]:
            indegree[i] -= 1
            if indegree[i] == 0:
                q.append(i)
                answer[i] = answer[now] + 1

topology_sort()
for x in answer[1:]:
    print(x, end=" ")
```