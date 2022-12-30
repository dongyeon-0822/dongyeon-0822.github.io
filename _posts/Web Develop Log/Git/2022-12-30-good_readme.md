---
title:  "[Git] 좋은 README를 작성하는 법" 

categories:
  - Git
tags:
  - [git, readme]

toc: true
toc_sticky: true
toc_label: "Content"
---


💡 프로젝트 레포지토리에 들어가면 가장 먼저 읽게 되는 것은 Readme.md이다. Readme는 프로젝트에 대해서 간단하고 명료하게 잘 설명되어 있어야 한다. Readme에 들어가야 할 내용들을 정리하여 나만의 프로젝트 Readme.md 템플릿을 만들어보자!
{: .notice--primary}

# 좋은 README를 작성하는 법

## 나만의 Readme.md Template

```markdown
# 프로젝트 소개 
프로젝트에 대한 설명을 간단하게 작성한다. 
프로젝트의 목적 및 용도를 주로 설명한다. 

## 프로젝트 추가 링크
프로젝트 배포 링크 (없다면 Getting start)
노션 링크 / 위키 링크 

## 프로젝트 개발환경 및 사용기술 
프로젝트 개발에 사용한 개발환경 또는 사용 기술들을 작성한다. 
ex)
IDE : IntelliJ
Language : Java 11
Framework : Springboot 2.7.5
Build : Gradle 7.5.1
Database : MySQL 8.0
CI & CD : GitLab
Server : AWS EC2
Deploy : Docker

## 사용 라이브러리
프로젝트에 사용한 라이브러리를 적는다. 
ex ) build.gradle에 dependency 내용

## 시스템 아키텍쳐 
인프라, FE, BE 구조를 사진 한장으로 표현하기 

## 데이터베이스 구조
ERD 설계하기 

## 주요 기능 설명
각 기능별 상세 내용

## 라이선스 정보
어떤 라이선스로 배포되는지 
프로젝트를 사용함에 있어 제약 조건이 있는지 (특허, 상업적 사용)
```

이 외의 상세 프로젝트의 내용은 wiki나 notion에 정리하여 링크를 걸어둔다. 

## Reference

[https://github.com/matiassingers/awesome-readme](https://github.com/matiassingers/awesome-readme)