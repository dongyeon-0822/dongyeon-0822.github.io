---
title: "[Algorithm] Shortest Path"
categories:
  - Algorithm
tags:
  - [algorithm, shortest_path]

toc: true
toc_sticky: true
toc_label: "Content"
toc_icon: "sticky-note"
---

📣<br>
본 포스트는 '이것이 취업을 위한 코딩 테스트다 with 파이썬'을 공부하고 작성하였습니다 :)    
click > [(이코테 2021) 이것이 취업을 위한 코딩 테스트다 with 파이썬](https://www.youtube.com/watch?v=m-9pAwq1o3w)
{: .notice--primary}

# Shortest Path

## 이론

**최단 경로(Shortest Path)** 알고리즘은 특정 지점까지 가장 빠르게 도달하는 방법을 찾는 알고리즘이다. 최단 경로 알고리즘 유형에는 다양한 종류가 있는데 상황에 맞는 효율적인 알고리즘이 이미 정립되어 있다. 

최단 경로 문제는 보통 그래프를 이용해 각 지점은 노드로, 지점간 연결된 도로는 간선으로 표현된다. ➡️ [**그래프의 표현 방식**](https://www.notion.so/DFS-BFS-df7989316bb14dcea96dbc6b0520762f)

최단 경로 알고리즘는 크게 3종류가 있다. 

- **다익스트라 알고리즘** : 한 지점에서 다른 특정 지점까지의 최단 경로를 구해야 하는 경우
- **플로이드 워셜 알고리즘** : 모든 지점에서 다른 모든 지점까지의 최단 경로를 모두 구해야 하는 경우
- **벨만 포드 알고리즘** : 간선의 가중치가 음수일 때, 한 노드에서 다른 노드까지의 최단 거리를 구하는 알고리즘

### 다익스트라 알고리즘

다익스트라 최단 경로 알고리즘은 **그래프에서 여러 개의 노드가 있을 때, 특정한 노드에서 출발하여 다른 노드로 가는 각각의 최단 경로**를 구해주는 알고리즘이다. 

다익스트라 알고리즘은 매번 가장 비용이 적은 노드를 선택하기 때문에 **그리디 알고리즘**으로 분류된다. 알고리즘의 원리는 다음과 같다. 

1️⃣ 출발 노드를 설정한다. 

2️⃣ 최단 거리 테이블을 초기화한다. 

3️⃣ 방문하지 않은 노드 중에서 최단 거리가 가장 짧은 노드를 선택한다. 

4️⃣ 해당 노드를 거쳐 다른 노드로 가는 비용을 계산하여 최단거리 테이블을 갱신한다 

5️⃣ 3-4과정을 반복한다. 

**구현 코드**

```python
def dijkstra(start, distance, graph):
    q = []
    heapq.heappush(q,(0,start))
    distance[start] = 0
    while q:
        dist, node = heapq.heappop(q)
        if distance[node] < dist: # 이미 처리한 적 있는 노드라면 무시
            continue
        for i in graph[node]: # 현재 노드와 연결된 노드들 확인
            cost = dist+i[1] # 거리 계산
            if cost < distance[i[0]]: # 현재 최단거리보다 작다면 갱신하고 힙에 push
                distance[i[0]] = cost
                heapq.heappush(q,(cost, i[0]))
```

**시간 복잡도**

- 최단 거리 테이블을 리스트로 구현했을 때 → $O(V^2)$
- 최단 거리 테이블을 우선순위 큐(heap)으로 구현했을 때 → $O(E*logV)$

### 플로이드 워셜 알고리즘

플로이드 워셜 알고리즘은 **모든 지점에서 다른 모든 지점까지의 최단 경로를 모두 구해야 하는 경우**에 사용할 수 있는 알고리즘으로 점화식에 맞게 동작하기 때문에 **다이나믹 프로그래밍**으로 볼 수 있다. 

다익스트라 알고리즘은 단계마다 방문하지 않은 노드 중에서 최단 거리를 가지는 노드를 하나씩 선택한다. 그리고 해당 노드를 거쳐 가는 경로를 확인하며 최단 거리 테이블(1차원 리스트)를 갱신하는 방식이다. 

플로이드 워셜 알고리즘은 단계마다 현재 노드를 거쳐 가는 모든 경로를 고려한다. 모든 노드에 대하여 다른 모든 노드로 가는 최단 거리 정보를 모두 담아야 하기 때문에 2차원의 최단 거리 테이블로 정보를 처리한다. 알고리즘의 원리는 다음과 같다. 

1️⃣ 현재 확인하고 있는 노드를 제외하고, N-1개의 노드 중에서 서로 다른 노드 (A, B) 쌍을 선택한다. 

2️⃣ A → 현재 노드 → B로 가는 비용을 확인하고 최단 거리를 갱신하다. 

각 단계에서 최단 거리를 갱신하는 점화식은 $D_{ab} = min(D_{ab}, D_{ak}+D_{kb})$ 이다. 

**구현 코드**

```python
for k in range(1,n+1):
    for i in range(1,n+1):
        for j in range(1,n+1):
            graph[i][j] = min(graph[i][j], graph[i][k]+graph[k][j])
```

**시간 복잡도**

N개의 노드에 대해서 $_{n-1}P_2$개의 쌍을 반복해서 확인하면 되므로 $O(N^3)$이라고 할 수 있다. 

### 벨만 포드 알고리즘

벨만 포드 알고리즘은 다익스트라 알고리즘과 똑같이 한 노드에서 다른 노드까지 최단 거리를 구하는 알고리즘이다. 차이점은 벨만 포드 알고리즘은 간선의 가중치가 음수일 때도 최단 거리를 구할 수 있다는 점이다. 알고리즘의 원리는 다음과 같다. 

1️⃣ 출발 노드를 설정한다. 

2️⃣ 최단 거리 테이블을 초기화한다. 

3️⃣ 모든 간선 E개를 하나씩 확인한다.

4️⃣ 해당 노드를 거쳐 다른 노드로 가는 비용을 계산하여 최단거리 테이블을 갱신한다 

5️⃣ 3-4과정을 반복한다. 

✅ **음수 간선 순환(cycle) 발생을 확인!**    
4️⃣번 과정을 한 번 더 수행하고 이때 최단 거리 테이블이 갱신되는지를 확인한다. 갱신되는 경우 음수 간선 순환이 존재한다는 것이다.   
음수 간선 순환이 존재하는 경우 비용을 무한히 줄일 수 있기 때문에 최단 거리를 수할 수 없게 되므로 꼭 확인해야 한다.
{: .notice--success}

**구현 코드**

```python
def bellmanFord(start):
    distance[start] = 0
    for i in range(v): # 전체 v - 1번 반복
        for j in range(e): # 매 반복마다 '모든 간선'을 확인한다.
            cur_node = edges[j][0]
            next_node = edges[j][1]
            edge_cost = edges[j][2]
            # 현재 간선을 거쳐서 다른 노드로 이동하는 거리가 더 짧은 경우
            if distance[cur_node] != INF and distance[next_node] > distance[cur_node] + edge_cost:
                distance[next_node] = distance[cur_node] + edge_cost
                # v번째 라운드에서도 값이 갱신된다면 음수 순환이 존재
                if i == v - 1:
                    return True
    return False
```

REF : [https://deep-learning-study.tistory.com/587](https://deep-learning-study.tistory.com/587) 

**시간 복잡도**

모든 노드에서 모든 간선을 확인하므로 **O(VE)**이다.

## 실전 **문제**

### [실전문제 1] 미래도시

```python
INF = int(1e9)

n, m = map(int, input().split())
graph = [[INF] * (n+1) for _ in range(n+1)]

for a in range(1,n+1):
		for b in range(1,n+1):
				if a == b: 
						graph[a][b] = 0 # 자기 자신 비용은 0으로 초기화

for _ in range(m):
		a, b = map(int, input().split())
		graph[a][b] = 1
		graph[b][a] = 1

x, k = map(int, input().split())

for k in range(1, n+1):
		for i in range(1, n+1):
				for j in range(1, n+1):
						graph[i][j] = min(graph[i][j], graph[i][k] + graph[k][j])

distance = graph[1][k] + graph[k][x]

if distance >= INF:
		print(-1)
else:
		print(distance)
```

### [실전문제 2] 전보

```python
import heapq
import sys
input = sys.stdin.readline
INF = int(1e9) # 무한을 의미하는 값으로 10억을 설정

# 노드의 개수, 간선의 개수, 시작 노드를 입력받기
n, m, start = map(int, input().split())
# 각 노드에 연결되어 있는 노드에 대한 정보를 담는 리스트를 만들기
graph = [[] for i in range(n + 1)]
# 최단 거리 테이블을 모두 무한으로 초기화
distance = [INF] * (n + 1)

# 모든 간선 정보를 입력받기
for _ in range(m):
    x, y, z = map(int, input().split())
    # X번 노드에서 Y번 노드로 가는 비용이 Z라는 의미
    graph[x].append((y, z))

def dijkstra(start):
   q = []
   # 시작 노드로 가기 위한 최단 경로는 0으로 설정하여, 큐에 삽입
   heapq.heappush(q, (0, start))
   distance[start] = 0
   while q: # 큐가 비어있지 않다면
        # 가장 최단 거리가 짧은 노드에 대한 정보를 꺼내기
        dist, now = heapq.heappop(q)
        if distance[now] < dist:
            continue
        # 현재 노드와 연결된 다른 인접한 노드들을 확인
        for i in graph[now]:
            cost = dist + i[1]
            # 현재 노드를 거쳐서, 다른 노드로 이동하는 거리가 더 짧은 경우
            if cost < distance[i[0]]:
                distance[i[0]] = cost
                heapq.heappush(q, (cost, i[0]))

# 다익스트라 알고리즘을 수행
dijkstra(start)

# 도달할 수 있는 노드의 개수
count = 0
# 도달할 수 있는 노드 중에서, 가장 멀리 있는 노드와의 최단 거리
max_distance = 0
for d in distance:
    # 도달할 수 있는 노드인 경우
    if d != 1e9:
        count += 1
        max_distance = max(max_distance, d)

# 시작 노드는 제외해야 하므로 count - 1을 출력
print(count - 1, max_distance)
```