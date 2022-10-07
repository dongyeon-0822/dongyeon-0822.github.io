---
title:  "[Data Structure] 자료구조 정리" 

categories:
  - Data_Structure
tags:
  - [data_structure]

toc: true
toc_sticky: true
toc_label: "Content"

date: 2022-10-03
last_modified_at: 2022-10-03
---

# 자료구조란?

프로그래밍에서 여러 데이터들의 묶음을 저장하고 사용하는 방법을 정의한 것으로 데이터를 구조적으로 표현하는 방식과 이를 구현하는 데 필요한 알고리즘에 대해 논하는 기초이론이다.  

잘 짜인 자료구조는 메모리 용량을 최소한으로 하고, 실행시간도 단축시킴으로써 보다 효율적인 알고리즘을 실행할 수 있게 한다. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1a49c3df-7204-4411-ba72-9cae253961e4/Untitled.png)

## 배열 (Array)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3598836a-f162-4e52-92c2-b89a18dd88f8/Untitled.png)

- 가장 기본적인 **선형 데이터 구조**이다.
- 한 가지 자료형의 데이터를 순차적으로 저장하는 자료구조
- 생성 시, 크기가 고정되고, 인덱스와 대응하는 데이터를 저장한다.
- 장점 : 인덱스를 통한 검색 연산이 빠르다.
- 단점 : 배열의 크기가 고정되어 있으며 추가/삭제 연산이 느리다.

## 연결리스트 (Linked List)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c2008e1e-f85a-4e10-952e-21b64bf2349f/Untitled.png)

- 배열의 단점이 보완된 형태의 자료구조로 배열의 크기가 가변적이다.
- **노드와 포인터**를 사용하여 데이터를 저장 및 연결한다.
- 노드(Node) : 데이터와 다음 노드의 주소를 가리키는 포인터 한 쌍으로 구성된다.
- 장점 : 배열의 크기가 가변적이며, 추가/삭제 연산을 할 때는 해당 노드의 포인터 주소만 변경해주면 된다.
- 단점 : 데이터를 삭제하면 데이터 연결을 재구성 해야하고, 인덱스를 참조할려면 첫번째 노드부터 접근해야 한다는 비효율성이 있다.
- 단순 연결리스트, 이중 연결리스트, 원형 연결리스트가 있다.

### 이중 연결리스트 (Double Linked List)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/da9d8bb3-b656-488a-be87-40d7f876eb40/Untitled.png)

- 노드가 데이터, 앞뒤 노드의 주소값을 가리키는 포인터로 구성되어 있는 연결 리스트이다.
- 장점 : 앞뒤 양방향으로 검색이 가능하다.

## 스택 (Stack)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/de2f3f79-3aa6-4230-9c8a-e829d8497474/Untitled.png)

- 순서가 유지되는 선형 자료구조의 일종
- 리스트의 한쪽에서만 데이터의 삽입과 삭제가 일어나는 **FILO(First In Last Out)** 메커니즘을 가지고 있다.
- 장점 : 구현이 단순하고 메모리 크기가 동적이며, 데이터의 저장 및 검색 속도가 빠르다.
- 단점 : 한 번에 하나의 데이터만 처리 가능하다.
- 프로세스의 실행구조의 기본으로 사용된다.

## 큐 (Queue)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8b8240fe-1f68-4e7a-a158-00892eb02bc8/Untitled.png)

- 순서가 유지되는 선형 자료구조의 일종
- Stack과 반대로 리스트의 한쪽에서는 삽입이 일어나고 다른 쪽에서는 삭제가 일어나는 **FIFO(First In First Out)** 메커니즘을 가지고 있다.
- 장점 : 메모리 크기가 동적이며, 데이터 삭제 시 재정렬이 필요없다.
- 단점 : 한 번에 하나의 데이터만 처리 가능하다.
- OS에서 프로세스 스케쥴링 방식 구현에 사용한다.

## 트리 (Tree)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43a19a51-de8d-4c92-aee1-319f0fd31ae9/Untitled.png)

- Stack, Queue와는 다르게 **비선형 자료구조**로, 노드와 브랜치를 이용하여 계층적 구조를 표현하는 자료구조이다.
- 그래프의 한 종류로 **사이클이 없는 하나의 연결 그래프(Connected Graph)** 또는 **방향성이 있는 비순환 그래프(Directed Acyclic Graph)**의 한 종류이다.
- Tree 용어
    - Node (노드) : 트리를 구성하고 있는 원소 그 자체를 말한다.
    - Edge (간선) : 노드와 노드사이를 연결하고 있는 선을 말한다. (=Link, branch)
    - Root node : 부모가 없는 노드, 트리는 하나의 루트 노드만을 가진다.
    - Leaf node : 자식이 없는 노드, ‘말단 노드’ 또는 ‘잎 노드’라고도 부른다.
    - Internal node : 단말 노드가 아닌 노드
- 트리를 기반으로 이진트리를 활용하여 탐색 알고리즘 구현에 자주 사용된다.
- 순회는 Pre-order, In-order 아니면 Post-order로 이루어진다. 이 3가지 모두 DFS/BFS 안에 있다.
- 트리는 이진 트리, 이진 탐색 트리, 균형 트리(AVL 트리, red-black 트리), 이진 힙(최대힙, 최소힙) 등이 있다.

### 이진트리 (Binary Tree)

- 각 노드가 최대 2개의 자식을 갖는 트리
- 이진 트리 순회
    - 중위 순회(in-order traversal) : 왼쪽 가지 → 현재 노드 → 오른쪽 가지
    - 전위 순회(pre-order traversal) : 현재 노드 → 왼쪽 가지 → 오른쪽 가지
    - 후위 순회(post-order traversal) : 왼쪽 가지 → 오른쪽 가지 → 현재 노드

### 이진 탐색 트리(Binary Search Tree)

- 이진트리를 기반으로 하여 좌측에는 우측에 위치한 노드보다 작은 값을 가지는 트리
- 이진탐색 트리는 검색에 용이하지만, 구현이 복잡하다.

### 균형 트리

- O(log N) 시간에 insert와 find를 할 수 있을 정도로 균형이 잘 잡혀 있는 경우 균형 트리라고 한다.
- 예시로 레드-블랙 트리, AVL 트리가 있다.

### 완전 이진 트리(Complete Binary Tree)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/21d40d7d-c9dc-4c56-95d7-bc01068e4fc7/Untitled.png)

- 트리의 모든 높이에서 노드가 꽉 차 있는 이진트리이다.
- 마지막 레벨을 제외하고 모든 레벨이 채워져 있어야 한다.
- 마지막 레벨은 노드가 왼쪽에서 오른쪽으로 채워져야 한다.

### 전 이진 트리(Full Binary Tree / Strictly Binary Tree)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/86fb37fd-4693-4fd1-a1e2-1cb63f37f2f1/Untitled.png)

- 모든 노드가 0개 또는 2개의 자식 노드를 갖는 트리

### 포화 이진 트리(Perfect Binary Tree)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2afaf118-afa2-49e7-b2ec-add031b31f64/Untitled.png)

- 전 이진 트리 이면서 완전 이진 트리인 트리이다.
- 모든 내부 노드가 2개의 자식 노드를 가진다.
- 모든 말단 노드가 동일한 깊이 또는 레벨을 가진다.

### 힙 (Heap)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/55d5add6-4225-4509-b0f0-ee05e7e0ac9a/Untitled.png)

- 트리구조를 기반으로 한 자료구조로 데이터에서 최대값과 최소값을 빠르게 찾기 위해 고안된 **완전 이진트리(Complete Binary Tree)** 이다.
- **우선순위 큐**를 위하여 만들어진 자료구조로 힙으로 우선순위 큐를 구현 시, 삽입과 삭제의 시간 복잡도는 O(log N)이다.
- 최소힙(Min Heap)
    - 부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리
    - **key(부모 노드) ≤ key(자식 노드)** 인 완전 이진 트리
    - 루트 노드에 가장 작은 값이 있다.
- 최대힙(Max Heap)
    - 부모 노드의 키 값이 자식 노드의 키 값보다 크거나 같은 완전 이진 트리
    - **key(부모 노드) ≥ key(자식 노드)** 인 완전 이진 트리
    - 루트 노드에 가장 큰 값이 있다.

## 그래프 (Graph)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8e68209f-c06c-4cc3-b84a-2bda8fe4243a/Untitled.png)

- 정점(Vertex)과 간선(Edge)로 이루어진 데이터 구조
- 탐색 방법에는 깊이 우선 탐색(DFS, Depth First Search)와 너비 우선 탐색(BFS, Breadth First Search)이 있다.
- 인접리스트나 인접 행렬로 구현할 수 있다.
- 장점 : 새로운 요소들의 추가/삭제에 용이하고, 구조의 응용이 가능하다.
- 단점 : 데이터 간의 충돌이 일어날 수 있다.
- 그래프의 종류로 방향/무방향 그래프, 가중치 그래프, 연결/비연결 그래프, 사이클 또는 비순환 그래프 등이 있다.

### 방향 그래프(Direct Graph) & 무방향 그래프(Undirected Graph)

- 방향 그래프(Directed Graph)
    - 간선에 방향성이 존재하는 그래프
    A → B로만 갈 수 있는 간선은 <A, B>로 표시한다.
    <A, B> ≠ <B, A>
- 무방향 그래프(Undirected Graph)
    - 무방향 그래프의 간선은 양 방향으로 갈 수 있다.
    정점 A와 정점 B를 연결하는 간선은 (A, B)와 같이 표현한다.
    (A, B) = (B, A)

### 가중치 그래프(Weighted Graph)

- 가중치 그래프(Weighted Graph)
    - 간선에 비용이나 가중치가 할당된 그래프
    - 네트워크(Network) 라고도 한다.

### 연결 그래프(Connected Graph) & 비연결 그래프(Unconnected Graph)

- 연결 그래프(Connected Graph)
    - 무방향 그래프에 있는 모든 정점쌍에 대해서 항상 경로가 존재하는 경우
- 비연결 그래프(Disconnected Graph)
    - 무방향 그래프에서 특정 정점쌍 사이에 경로가 존재하지 않는 경우

### 사이클(Cycle) & 비순환 그래프(Acyclic Graph)

- 사이클(Cycle)
    - 단순 경로의 시작 정점과 종료 정점이 동일한 경우
- 비순환 그래프(Acyclic Graph)
    - 사이클이 없는 그래프

### 그래프와 트리의 차이점

![출처 - [https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html)](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ad39ee21-df64-400e-92b6-2ee4cc7e9392/Untitled.png)

출처 - [https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html)

## 해시 테이블 (Hash Table)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e53fc6bd-24d9-46c5-9439-85acc8801489/Untitled.png)

- **Key와 Value를 한 쌍**으로 저장하는 자료구조
- 평균적으로 충돌이 고려하지 않았을 때, 빠른 탐색속도 O(1)을 갖는다.
- Key를 Hash 함수에 적용하여 나온 결과 값을 인덱스로 하여 해당 인덱스에 Value를 집어 넣는다.
- 장점 : Key를 이용하여 Value를 빠르게 검색할 수 있고, 데이터의 중복을 쉽게 확인할 수 있다.
- 단점 : 저장공간을 많이 필요로 하고 충돌이 일어날 수 있다.
- 충돌 해소법(Resolve Conflict)
    - **Chaining** : Open Hashing기법 중 하나로, 해시테이블의 저장공간 이외의 공간을 활용하는 기법이다. 만약 해시충돌이 발생하면, 연결리스트를 사용하여 데이터를 추가로 연결시키는 저장방법이다.
    - **Linear Probing** : Close Hashing기법 중 하나로, 해시테이블의 저장공간 안에서 충돌을 해결하는 기법이다. 만약 해시충돌이 발생하면, 해시값(해시주소)을 이용하여 해시테이블 내부의 빈자리를 찾아 저장하는 기법이다.

## 시간복잡도 정리

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9d42a9f3-b127-4a4f-8b4a-3f185cd2bd77/Untitled.png)