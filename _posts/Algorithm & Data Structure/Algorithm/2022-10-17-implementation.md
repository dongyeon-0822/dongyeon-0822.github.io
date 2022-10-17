---
title: "[Algorithm] Implementation"
categories:
  - Algorithm
tags:
  - [algorithm, implementation]

toc: true
toc_sticky: true
toc_label: "Content"
toc_icon: "sticky-note"
---

📣<br>
본 포스트는 '이것이 취업을 위한 코딩 테스트다 with 파이썬'을 공부하고 작성하였습니다 :)    
click > [(이코테 2021) 이것이 취업을 위한 코딩 테스트다 with 파이썬](https://www.youtube.com/watch?v=m-9pAwq1o3w)
{: .notice--primary}

# Implementation

## 이론

구현이란 **‘머릿속에 있는 알고리즘을 소스코드로 바꾸는 과정’**이다. 

**완전 탐색(Brute Force), 시뮬레이션(Simulation)** 유형을 모두 구현 유형으로 묶어서 다룬다. 완전 탐색은 모든 경우의 수를 주저 없이 다 계산하는 해결 방법을 의미하고, 시뮬레이션은 문제에서 제시한 알고리즘을 한 단계씩 차례대로 직접 수행하는 문제 유형이다. 

**구현 시 고려해야 할 메모리 제약 사항**

C/C++ 와 자바에서 정수형 종류에 따른 범위

| 정수형 종류 | 자료형의 크기 | 자료형의 범위 |
| --- | --- | --- |
| int | 4byte | -2,147,483,648 ~ 2,147,483,647 |
| long long | 8byte | -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 |
| BigInteger(class) | 가변적 | 제한 없음 |

파이썬에서 int 자료형 데이터의 개수에 따른 메모리 사용량

| 데이터 개수(리스트의 길이) | 메모리 사용량 |
| --- | --- |
| 1,000 | 약 4KB |
| 1,000,000 | 약 4MB |
| 10,000,000 | 약 40MB |

보통 코딩 테스트에서 128 ~ 512MB 정도 메모리 제한을 둔다. 파이썬은 데이터 처리량이 많을 때는 메모리 제한이 걸릴 수 있으니 주의 하자!

### [예제 4-1] 상하좌우

```python
N = int(input())
x, y = 1, 1
plans = input().split()

dx = [0, 0, -1, 1]
dy = [-1, 1, 0, 0]
move_type = ['L', 'R', 'U', 'D']

for plan in plans:
    for i in range(len(move_type)):
        if plan == move_type[i]:
            nx = x + dx[i]
            ny = y + dy[i]
    if nx <1 or ny < 1 or nx > N or ny > N:
        continue
    x, y = nx, ny

print(x,y)
```

### [예제 4-2] 시각

```python
H = int(input())

count = 0
for i in range(H + 1):
    for j in range(60):
        for k in range(60):
            if '3' in str(i) + str(j) + str(k):
                count += 1
print(count)
```

## 실전문제

### [실전문제 1] 왕실의 나이트

```python
input_data = input()
row = int(input_data[1])
column = int(ord(input_data[0])) - int(ord('a')) + 1

steps = [(-2, -1), (-1, -2), (1, -2), (2, -1), (2, 1), (1, 2), (-1, 2), (-2, 1)]

result = 0
for s in steps:
    next_row = row + s[0]
    next_column = column + s[1]
    if 1 <= next_row <= 8 and 1 <= next_column <= 8:
        result += 1
print(result)
```

### [실전문제 2] 게임 개발

```python
# 정보 입력받기
N, M = map(int, input().split())
A, B, direct = list(map(int, input().split()))
maps = []
for _ in range(N):
    maps.append(list(map(int, input().split())))

visited = [[0] * M for _ in range(N)]
visited[A][B] = 1
move = [(-1, 0), (0, 1), (1, 0), (0, -1)]

def turn_left():
    global direct
    direct -= 1
    if direct < 0:
        direct = 3

count = 1
turns = 0
while True:
    turn_left()
    a = A + move[direct][0]
    b = B + move[direct][1]
    if 0 <= a < N and 0 <= b < M and visited[a][b] == 0 and maps[a][b] == 0:
        A = a
        B = b
        visited[a][b] = 1
        count += 1
        turns = 0
        continue
    else:
        turns += 1
    if turns == 4: # 다시 원래 방향
        a = A - move[direct][0]
        b = B - move[direct][0]
        if maps[a][b] == 0:
            A = a
            B = b
            turns = 0
        else:
            break
print(count)
```