---
title: "[Algorithm] Binary Search"
categories:
  - Algorithm
tags:
  - [algorithm, binary_search]

toc: true
toc_sticky: true
toc_label: "Content"
toc_icon: "sticky-note"
---

📣<br>
본 포스트는 '이것이 취업을 위한 코딩 테스트다 with 파이썬'을 공부하고 작성하였습니다 :)    
click > [(이코테 2021) 이것이 취업을 위한 코딩 테스트다 with 파이썬](https://www.youtube.com/watch?v=m-9pAwq1o3w)
{: .notice--primary}

# Binary Search

## 이론

**순차 탐색(Sequential Search)**은 리스트 안에 있는 특정한 데이터를 찾기 위해 앞에서부터 데이터를 차례대로 확인하는 방법이다. 

**이진 탐색(Binary Search)**는 배열 내부의 데이터가 정렬되어 있을 때, 위치를 나타내는 변수 3개(시작점, 끝점, 중간점)을 이용하여 중간점과 찾고자 하는 데이터를 반복적으로 비교하여 데이터를 찾는 방법이다. 또한 이진 탐색 문제는 탐색범위가 튼 상황에서 탐색을 가정하는 문제가 많다. 탐색 범위가 2000만을 넘어가는 경우 이진탐색으로 접근하는 것이 좋다. 

이진 탐색 알고리즘은 한 단계를 거칠 때마다 확인하는 원소가 평균적으로 절반으로 줄어들기 때문에 시간복잡도는 O(logN)이다. 

**재귀함수로 구현한 이진탐색**

```python
# 이진 탐색 소스코드 구현 (재귀 함수)
def binary_search(array, target, start, end):
    if start > end:
        return None
    mid = (start + end) // 2
    # 찾은 경우 중간점 인덱스 반환
    if array[mid] == target:
        return mid
    # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
    elif array[mid] > target:
        return binary_search(array, target, start, mid - 1)
    # 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
    else:
        return binary_search(array, target, mid + 1, end)

# n(원소의 개수)과 target(찾고자 하는 값)을 입력 받기
n, target = list(map(int, input().split()))
# 전체 원소 입력 받기
array = list(map(int, input().split()))

# 이진 탐색 수행 결과 출력
result = binary_search(array, target, 0, n - 1)
if result == None:
    print("원소가 존재하지 않습니다.")
else:
    print(result + 1)
```

**반복문으로 구현한 이진 탐색** 

```python
# 이진 탐색 소스코드 구현 (반복문)
def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        # 찾은 경우 중간점 인덱스 반환
        if array[mid] == target:
            return mid
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        elif array[mid] > target:
            end = mid - 1
        # 중간점의 값보다 찾고자 하는 값이 큰 경우 오른쪽 확인
        else:
            start = mid + 1
    return None

# n(원소의 개수)과 target(찾고자 하는 값)을 입력 받기
n, target = list(map(int, input().split()))
# 전체 원소 입력 받기
array = list(map(int, input().split()))

# 이진 탐색 수행 결과 출력
result = binary_search(array, target, 0, n - 1)
if result == None:
    print("원소가 존재하지 않습니다.")
else:
    print(result + 1)
```

**이진 탐색 트리**

큰 데이터를 처리하는 소프트웨어에서는 대부분 데이터를 트리 자료구조로 저장해서 이진 탐색과 같은 탐색 기법을 이용해 빠르게 탐색을 한다. 이진 탐색 트리는 트리 자료구조 중에서도 이진 탐색이 동작할 수 있도록 고안된, 효율적인 탐색이 가능한 자료구조이다. 

![image](https://user-images.githubusercontent.com/68420044/208289822-bba80ae2-2876-4ae6-a97e-95af04878ea6.png)


이진 탐색 트리는 다음과 같은 특징을 가진다. 

- 부모 노드보다 왼쪽 자식 노드가 작다.
- 부모 노드보다 오른쪽 자식 노드가 크다.

## 실전 문제

### [실전문제 1] 부품 찾기

- **이진 탐색으로 구현**

```python
def binary_search(array, target, start, end):
    while start <= end:
        mid = (start + end) // 2
        # 찾은 경우 중간점 인덱스 반환
        if array[mid] == target:
            return mid
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 왼쪽 확인
        elif array[mid] > target:
            end = mid - 1
        # 중간점의 값보다 찾고자 하는 값이 작은 경우 오른쪽 확인
        else:
            start = mid + 1
    return None

# N(가게의 부품 개수) 입력
n = int(input())
# 가게에 있는 전체 부품 번호를 공백을 기준으로 구분하여 입력
array = list(map(int, input().split()))
array.sort() # 이진 탐색을 수행하기 위해 사전에 정렬 수행
# M(손님이 확인 요청한 부품 개수) 입력
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백을 기준으로 구분하여 입력
x = list(map(int, input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    result = binary_search(array, i, 0, n - 1)
    if result != None:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```

- **계수 정렬을 활용하여 구현**

```python
# N(가게의 부품 개수) 입력
n = int(input())
array = [0] * 1000001

# 가게에 있는 전체 부품 번호를 입력 받아서 기록
for i in input().split():
    array[int(i)] = 1

# M(손님이 확인 요청한 부품 개수) 입력
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백을 기준으로 구분하여 입력
x = list(map(int, input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    if array[i] == 1:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```

- **집합 자료형을 이용하여 구현**

```python
# N(가게의 부품 개수) 입력
n = int(input())
# 가게에 있는 전체 부품 번호를 입력 받아서 집합(Set) 자료형에 기록
array = set(map(int, input().split()))

# M(손님이 확인 요청한 부품 개수) 입력
m = int(input())
# 손님이 확인 요청한 전체 부품 번호를 공백을 기준으로 구분하여 입력
x = list(map(int, input().split()))

# 손님이 확인 요청한 부품 번호를 하나씩 확인
for i in x:
    # 해당 부품이 존재하는지 확인
    if i in array:
        print('yes', end=' ')
    else:
        print('no', end=' ')
```

### [실전문제 2] 떡볶이 떡 만들기

```python
n, m = map(int, input().split())
array = list(map(int, input().split()))

start = 0
end = max(array)

answer = 0
while start <= end:
		mid = (start + end) // 2 
		value = 0
		for a in array:
				if a > mid:
						value += (a - mid)
		if value < m :
				end = mid - 1
		else:
				answer = mid # 최대한 덜 잘랐을 때가 정답이므로, 우선 answer에 저장
				start = mid + 1

print(answer)
```
