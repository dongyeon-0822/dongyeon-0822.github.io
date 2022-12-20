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

## Commit Message 의 구성 방법

```
<type>[optional scope]: <description>  -- 제목

[optional body]                        -- 본문

[optional footer(s)]                   -- 바닥글
```

1. 제목 : 어떤 것을 했는지 핵심 내용을 명확하게 적는다. 
2. 본문 : 자세한 커밋 메시지를 작성하고자 할 때, 제목에 이어 부가적인 설명을 작성한다. (커밋 이유, 변경 내용 등)
3. 바닥글: 주로 관련 이슈 번호를 참조할 때 사용한다. 

## 커밋 유형

| COMMIT TYPE | 뜻 |
| --- | --- |
| Feat | 새로운 기능의 추가  |
| Fix | 버그 수정  |
| Chore | feat이나 fix와 관련 없는 변경 사항, src나 test 파일이 아닌 다른 파일 수정 사항 
(ex .dependencies 수정 같은 경우) |
| Refactor | 버그를 고치거나 새로운 기능 추가가 아닌 코드 리팩토링  |
| Docs | 문서 수정 (README.md) |
| Style | 스타일 관련 코드 (코드 포맷팅, 세미콜론 누락, 코드 자체의 변경이 없는 경우) |
| Test | 테스트 코드, 리펙토링 테스트 코드  |
| Perf | 기능 개선 코드 추가  |
| Ci | CI/CD 관련 코드 |
| Build | 빌드 시스템이나 외부 종속성과 관련있는 코드  |
| Delete | 코드 삭제 |
| Remove | 파일 삭제 |
| Rename | 파일이나 디렉토리 명 수정 |
| Move | 파일위치 이동 |




## Reference

- [How to Write Better Git Commit Messages - A Step-By-Step Guide](https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/)

- [좋은 git 커밋 메시지를 작성하기 위한 7가지 약속 : NHN Cloud Meetup](https://meetup.toast.com/posts/106)