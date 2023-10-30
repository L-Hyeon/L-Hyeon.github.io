---
layout: post
title: 2. GIT
categories: OpenSource
tags: [CS, OpenSource]
---

## Git?

> 오픈소스 분산 버전 관리 시스템
> {: .prompt-tip }

### 구조

##### Working Tree

- 실제 작업을 진행하는 위치
- 수정, 저장이 발생

##### Stage

- 버전 관리를 수행할 대상 저장

##### Repository

- 각 버전이 실제로 저장되어 있는 위치

### 명령어

- git init
- git add [파일명]
- git commit -m [메시지]
- git status
- git log
- git branch [새로운 브랜치]
- git checkout [브랜치]
- git branch -m [변경할 이름]
- git branch -d [삭제할 브랜치]
- git merge [합병할 대상]
- git remote add [원격 이름] [원격 주소]
- git push [원격 이름] [로컬 브랜치]
- git pull [원격 이름] [로컬 브랜치]
