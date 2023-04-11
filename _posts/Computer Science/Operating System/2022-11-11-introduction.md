---
title:  "[Operating System] Chapter1. Introduction to Operating System" 

categories:
  - Operating_System
tags:
  - [computer_science, operating_system]

toc: true
toc_sticky: true
toc_label: "Content"
toc_icon: "sticky-note"
---

KOCW 이화여자대학교 반효경 교수님의 운영체제 강의를 듣고 정리한 포스트입니다! :)  
click > [KOCW-운영체제(반효경, 2014)](http://www.kocw.net/home/enrolment/enrolmentView.do?cid=3646706b4347ef09&lid=af8e05c97c6d60de)
{: .notice--primary}

> **배우는 내용** ✏️
> 
> 
> 운영체제란 무엇인가, 운영체제의 목적, 운영체제의 분류, 운영체제의 예, 운영체제의 구조
> 

# 강의 목차

| 운영체제 강의 목차 |
| --- |
| 1. 운영체제 개요 |
| 2. 컴퓨터시스템의 구조 |
| 3. 프로세스 관리 |
| 4. CPU 스케줄링 |
| 5. 병행 제어 |
| 6. 데드락 |
| 7. 메모리 관리 |
| 8. 가상 메모리 |
| 9. 입출력 시스템 |
| 10. 디스크 관리 |    


<br>


# 운영체제란 무엇인가?

## 운영체제(Operating System, OS)란?

- 컴퓨터 하드웨어 바로 위에 설치되어 사용자 및 다른 모든 소프트웨어와 하드웨어를 연결하는 소프트웨어 계층이다.

![image](https://user-images.githubusercontent.com/68420044/202338214-5e45f493-b646-4ecd-be60-0e3f89d3ff4a.png){: width="300" height="300"}


- 좁은 의미의 운영체제(커널)
    - 운영체제의 핵심 부분으로 메모리에 상주하는 부분
- 넓은 의미의 운영체제
    - 커널 뿐만 아니라 각종 주변 시스템 유틸리티를 포함한 개념

## 운영체제의 목적

- 컴퓨터 시스템을 편리하게 사용할 수 있는 환경 제공
- 컴퓨터 시스템의 **자원을 효율적으로 관리**
    - 프로세서(CPU), 기억장치(Memory), 입출력 장치(IO) 등의 효율적 관리
        - 사용자 간의 형평성 있는 자원 분배 = 형평성
        - 주어진 자원으로 최대한의 성능을 내도록 = 효율성
        - CPU : 실행 중인 프로그램들에게 짧은 시간씩 CPU를 번갈아 할당
        - Memory : 실행 중인 프로그램들에 메모리 공간을 적절히 분배
    - 사용자 및 운영체제 자신의 보호
    - 프로세스, 파일, 메시지 등을 관리
    
{% capture notice-2 %}
📝 **자원(Resource)**  
- **하드웨어 자원** : 프로세서(CPU), 기억장치(Memory), 입출력 장치(IO)  
- **소프트웨어 자원** : 프로세스, 파일, 메시지
{% endcapture %}
<div class="notice">{{ notice-2 | markdownify }}</div>
    

## 운영체제의 분류

> **분류 기준**
> 
> 1. 동시 작업 가능 여부
> 2. 사용자의 수
> 3. 처리 방식

### 1. 동시 작업 가능 여부

- **단일 작업 (Single tasking)**
    
    한 번에 하나의 작업만 처리 → 과거의 운영체제 방식
    
- **다중 작업 (Multi tasking)**
    
    동시에 두 개 이상의 작업 처리 → 현재 운영체제 방식    
    Unix, MS Windows 등
    

### 2. 사용자의 수

- **단일 사용자 (Single User)**
- **다중 사용자 (Multi User)**

### 3. 처리방식

- **일괄처리 (batch processing)**
    
    작업 요청의 일정량을 모아서 한꺼번에 처리
    
    작업이 완전 종료될 때까지 기다려야 한다. 
    

> [https://core.ewha.ac.kr/publicview/C0101020140307151724641842?vmode=f](https://core.ewha.ac.kr/publicview/C0101020140307151724641842?vmode=f)  16:00
>