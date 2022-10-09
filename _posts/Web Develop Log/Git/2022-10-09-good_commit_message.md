---
title:  "[Git] 좋은 커밋 메시지를 작성하는 법" 

categories:
  - Git
tags:
  - [git]

toc: true
toc_sticky: true
toc_label: "Content"

date: 2022-10-09
last_modified_at: 2022-10-09
---


💡 개발자라면 Git은 필수로 사용할 줄 알아야 한다. Git은 주로 협업을 할 때는 필수로 사용하게 되는데, 이때 commit message는 팀 간의 의사소통에 중요한 역할을 하기 때문에 좋은 commit message를 작성하는 법을 배우고자 한다!
{: .notice--primary}



# 좋은 커밋 메시지를 작성하는 법

## 좋은 git 커밋 메시지를 작성하기 위한 7가지 약속

1. 제목과 본문을 한 줄 띄워 분리하기
2. 제목은 영문 기준 50자 이내로
3. 제목 첫글자를 대문자로
4. 제목 끝에 `.` 금지
5. 제목은 `명령조`로
6. 본문은 영문 기준 72자마다 줄 바꾸기
7. 본문은 `어떻게`보다 `무엇을`, `왜`에 맞춰 작성하기

## 커밋 명령어 정리

내가 주로 쓰는 커밋 메시지를 정리해 보았다. 

| 커밋 명령어 | 뜻 |
| --- | --- |
| Create | 새로운 파일 생성 및 추가 |
| Add | 코드나 테스트, 예제, 문서 등의 추가 |
| Modify | 코드 보완 및 수정 |
| Fix | 올바르지 않은 동작을 수정 |
| Delete | 코드 삭제 |
| Rename | 파일이나 디렉토리 명 수정 |
| Move | 파일위치 이동 |
| Remove | 파일 삭제 |



## Reference

- [좋은 git 커밋 메시지를 작성하기 위한 7가지 약속 : NHN Cloud Meetup](https://meetup.toast.com/posts/106)