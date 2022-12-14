---
title: "[Algorithm] Dynamic Programming"
categories:
  - Algorithm
tags:
  - [algorithm, dynamic_programming]

toc: true
toc_sticky: true
toc_label: "Content"
toc_icon: "sticky-note"
---

π£<br>
λ³Έ ν¬μ€νΈλ 'μ΄κ²μ΄ μ·¨μμ μν μ½λ© νμ€νΈλ€ with νμ΄μ¬'μ κ³΅λΆνκ³  μμ±νμμ΅λλ€ :)    
click > [(μ΄μ½ν 2021) μ΄κ²μ΄ μ·¨μμ μν μ½λ© νμ€νΈλ€ with νμ΄μ¬](https://www.youtube.com/watch?v=m-9pAwq1o3w)
{: .notice--primary}

# Dynamic Programming

## μ΄λ‘ 

μ°λ¦¬λ λ¬Έμ λ₯Ό ν΄κ²°ν  λ μ°μ° μλμ λ©λͺ¨λ¦¬ κ³΅κ°μ μ΅λνμΌλ‘ νμ©ν  μ μλ ν¨μ¨μ μΈ μκ³ λ¦¬μ¦μ μμ±ν΄μΌ νλ€. 

μ΄λ€ λ¬Έμ λ λ©λͺ¨λ¦¬ κ³΅κ°μ μ½κ° λ νμ©νλ©΄ μ°μ° μλλ₯Ό λΉμ½μ μΌλ‘ μ¦κ°μν¬ μ μλ λ°©λ²μ΄ μλ€. λνμ μΈ λ°©λ²μ΄ λ°λ‘ **λ€μ΄λλ―Ή νλ‘κ·Έλλ° (Dynamic Programming)** μ΄λ€. λ€μ΄λλ―Ή νλ‘κ·Έλλ°μ ν° λ¬Έμ λ₯Ό μκ² λλκ³ , κ°μ λ¬Έμ λΌλ©΄ ν λ²μ©λ§ νμ΄ λ¬Έμ λ₯Ό ν¨μ¨μ μΌλ‘ ν΄κ²°νλ μκ³ λ¦¬μ¦ κΈ°λ²μΌλ‘ λμ  κ³νλ²μ΄λΌκ³  νννκΈ°λ νλ€. 

λ€μ΄λλ―Ή νλ‘κ·Έλλ°μΌλ‘ ν΄κ²°ν  μ μλ λνμ μΈ μμλ‘ νΌλ³΄λμΉ μμ΄κ³Ό ν©ν λ¦¬μΌμ΄ μλ€. λ μμ λͺ¨λ μμ΄μ ν­μ μ νμμ μ΄μ©νμ¬ κ°λ¨νκ² μ μν  μ μλ€λ νΉμ§μ΄ μλ€. μ μλ λ μμλ₯Ό λͺ¨λ μ¬κ·ν¨μλ₯Ό μ΄μ©νμ¬ κ΅¬ννμλλ°, μ¬κ·ν¨μλ₯Ό μ¬μ©νκ² λλ©΄ nμ΄ μ»€μ§ μλ‘ μν μκ°μ΄ κΈ°νκΈμμ μΌλ‘ μ¦κ°νλ€λ λ¬Έμ μ μ΄ μλ€. (μκ° λ³΅μ‘λκ° μ½ O(2^n)μ΄λ€.) μ΄μ²λΌ μ νμμ μ¬κ· ν¨μλ₯Ό μ¬μ©ν΄ κ΅¬νν  μλ μμ§λ§, λ§€λ² κ³μ°νλλ‘ νλ€λ©΄ ν¨μ¨μ μΌλ‘ λ¬Έμ λ₯Ό ν΄κ²°ν  μ μλ€. λ°λΌμ μ΄λ¬ν λ¬Έμ λ λ€μ΄λλ―Ή νλ‘κ·Έλλ°μ μ¬μ©νμ¬ ν¨μ¨μ μΌλ‘ ν΄κ²°νλ€. λ€μ΄λλ―Ή νλ‘κ·Έλλ°μ λ€μ μ‘°κ±΄μ λ§μ‘±ν΄μΌ νλ€. 

1. ν° λ¬Έμ λ₯Ό μμ λ¬Έμ λ‘ λλ μ μλ€. 
2. μμ λ¬Έμ μμ κ΅¬ν μ λ΅μ κ·Έκ²μ ν¬ν¨νλ ν° λ¬Έμ μμλ λμΌνλ€. 

 λ€μ΄λλ―Ή νλ‘κ·Έλλ°μ κ΅¬ννλ λ°©λ² μ€ νλλ‘ λ©λͺ¨μ΄μ μ΄μ (Memorization) κΈ°λ²μ΄ μλ€. λ©λͺ¨μ΄μ μ΄μ κΈ°λ²μ κ°μ μ μ₯νλ λ°©μμΌλ‘ μΊμ±(Caching)μ΄λΌκ³ λ νλ©°, ν λ² κ΅¬ν κ²°κ³Όλ₯Ό λ©λͺ¨λ¦¬ κ³΅κ°μ μ μ₯ν΄λκ³  κ°μ μμ λ€μ νΈμΆνλ©΄ λ©λͺ¨ν κ²°κ³Όλ₯Ό κ·Έλλ‘ κ°μ Έμ€λ κΈ°λ²μ μλ―Ένλ€. 

λ€μ΄λλ―Ή νλ‘κ·Έλλ°μλ ν¬κ² 2κ°μ§ κ΅¬ν λ°©λ²μ΄ μλ€. 

1. **νλ€μ΄ (Top-Down) λ°©μ** 
    
    μ¬κ·ν¨μλ₯Ό μ΄μ©νμ¬ λ€μ΄λλ―Ή νλ‘κ·Έλλ° μμ€μ½λλ₯Ό μμ±νλ λ°©λ²μ ν° λ¬Έμ λ₯Ό ν΄κ²°νκΈ° μν΄ μμ λ¬Έμ λ€μ νΈμΆνλ€κ³  νμ¬ νλ€μ΄ λ°©μμ΄λΌκ³  νλ€. νλ€μ΄ λ°©μμ νν₯μμ΄λΌκ³ λ νλ©° λ©λͺ¨μ΄μ μ΄μ λ°©μμ μ¬μ©νλ€. 
    
    **νΌλ³΄λμΉ μμ΄ νλ€μ΄ λ°©μμΌλ‘ κ΅¬ν (λ©λͺ¨μ΄μ μ΄μ)**
    
    ```python
    # ν λ² κ³μ°λ κ²°κ³Όλ₯Ό λ©λͺ¨μ΄μ μ΄μ(Memoization)νκΈ° μν λ¦¬μ€νΈ μ΄κΈ°ν
    d = [0] * 100
    
    # νΌλ³΄λμΉ ν¨μ(Fibonacci Function)λ₯Ό μ¬κ·ν¨μλ‘ κ΅¬ν (νλ€μ΄ λ€μ΄λλ―Ή νλ‘κ·Έλλ°)
    def fibo(x):
        # μ’λ£ μ‘°κ±΄(1 νΉμ 2μΌ λ 1μ λ°ν)
        if x == 1 or x == 2:
            return 1
        # μ΄λ―Έ κ³μ°ν μ  μλ λ¬Έμ λΌλ©΄ κ·Έλλ‘ λ°ν
        if d[x] != 0:
            return d[x]
        # μμ§ κ³μ°νμ§ μμ λ¬Έμ λΌλ©΄ μ νμμ λ°λΌμ νΌλ³΄λμΉ κ²°κ³Ό λ°ν
        d[x] = fibo(x - 1) + fibo(x - 2)
        return d[x]
    
    print(fibo(99))
    ```
    
2. **λ³΄νμ(Bottom-Up) λ°©μ**
    
    λ¨μν λ°λ³΅λ¬Έμ μ΄μ©νμ¬ μμ€μ½λλ₯Ό μμ±νλ κ²½μ° μμ λ¬Έμ λΆν° μ°¨κ·Όμ°¨κ·Ό λ΅μ λμΆνλ€κ³  νμ¬ λ³΄νμ(Bottom-Up) λ°©μμ΄λΌκ³  νλ€. μ¬κ·ν¨μλ₯Ό μ¬μ©νλ νλ€μ΄ λ°©μλ³΄λ€ μ±λ₯μ΄ λ μ’λ€. λ€μ΄λλ―Ή νλ‘κ·Έλλ°μ μ νμ μ ννλ λ³΄νμ λ°©μμ΄κ³ , λ³΄νμ λ°©μμμ μ¬μ©λλ κ²°κ³Ό μ μ₯μ© λ¦¬μ€νΈλ DP νμ΄λΈμ΄λΌκ³  λΆλ₯Έλ€. 
    
    **νΌλ³΄λμΉ μμ΄ λ³΄νμ λ°©μμΌλ‘ κ΅¬ν**
    
    ```python
    # μμ κ³μ°λ κ²°κ³Όλ₯Ό μ μ₯νκΈ° μν DP νμ΄λΈ μ΄κΈ°ν
    d = [0] * 100
    
    # μ²« λ²μ§Έ νΌλ³΄λμΉ μμ λ λ²μ§Έ νΌλ³΄λμΉ μλ 1
    d[1] = 1
    d[2] = 1
    n = 99
    
    # νΌλ³΄λμΉ ν¨μ(Fibonacci Function) λ°λ³΅λ¬ΈμΌλ‘ κ΅¬ν(λ³΄νμ λ€μ΄λλ―Ή νλ‘κ·Έλλ°)
    for i in range(3, n + 1):
        d[i] = d[i - 1] + d[i - 2]
    
    print(d[n])
    ```
    

**λ€μ΄λλ―Ή νλ‘κ·Έλλ° λ¬Έμ  νμ΄ λ¨κ³**

1. λ€μ΄λλ―Ή νλ‘κ·Έλλ° μ νμμ νμνκΈ° 
2. λ³μ κ° κ΄κ³μ λ§λ€κΈ°(μ νμ)
3. κ΅¬ννκΈ°(memoization or tabulation) 

## μ€μ  λ¬Έμ 

### [μ€μ λ¬Έμ  1] 1λ‘ λ§λ€κΈ°

```python
# μ μ Xλ₯Ό μλ ₯ λ°κΈ°
x = int(input())

# μμ κ³μ°λ κ²°κ³Όλ₯Ό μ μ₯νκΈ° μν DP νμ΄λΈ μ΄κΈ°ν
d = [0] * 1000001

# λ€μ΄λλ―Ή νλ‘κ·Έλλ°(Dynamic Programming) μ§ν(λ³΄νμ)
for i in range(2, x + 1):
    # νμ¬μ μμμ 1μ λΉΌλ κ²½μ°
    d[i] = d[i - 1] + 1
    # νμ¬μ μκ° 2λ‘ λλμ΄ λ¨μ΄μ§λ κ²½μ°
    if i % 2 == 0:
        d[i] = min(d[i], d[i // 2] + 1)
    # νμ¬μ μκ° 3μΌλ‘ λλμ΄ λ¨μ΄μ§λ κ²½μ°
    if i % 3 == 0:
        d[i] = min(d[i], d[i // 3] + 1)
    # νμ¬μ μκ° 5λ‘ λλμ΄ λ¨μ΄μ§λ κ²½μ°
    if i % 5 == 0:
        d[i] = min(d[i], d[i // 5] + 1)

print(d[x])
```

### [μ€μ λ¬Έμ  2] κ°λ―Έ μ μ¬

```python
# μ μ Nμ μλ ₯ λ°κΈ°
n = int(input())
# λͺ¨λ  μλ μ λ³΄ μλ ₯ λ°κΈ°
array = list(map(int, input().split()))

# μμ κ³μ°λ κ²°κ³Όλ₯Ό μ μ₯νκΈ° μν DP νμ΄λΈ μ΄κΈ°ν
d = [0] * 100

# λ€μ΄λλ―Ή νλ‘κ·Έλλ°(Dynamic Programming) μ§ν (λ³΄νμ)
d[0] = array[0]
d[1] = max(array[0], array[1]) 
for i in range(2, n):
    d[i] = max(d[i - 1], d[i - 2] + array[i])

# κ³μ°λ κ²°κ³Ό μΆλ ₯
print(d[n - 1])
```

### [μ€μ λ¬Έμ  3] λ°λ₯ κ³΅μ¬

```python
# μ μ Nμ μλ ₯ λ°κΈ°
n = int(input())

# μμ κ³μ°λ κ²°κ³Όλ₯Ό μ μ₯νκΈ° μν DP νμ΄λΈ μ΄κΈ°ν
d = [0] * 1001

# λ€μ΄λλ―Ή νλ‘κ·Έλλ°(Dynamic Programming) μ§ν (λ³΄νμ)
d[1] = 1
d[2] = 3
for i in range(3, n + 1):
    d[i] = (d[i - 1] + 2 * d[i - 2]) % 796796

# κ³μ°λ κ²°κ³Ό μΆλ ₯
print(d[n])
```