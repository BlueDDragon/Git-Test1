# 📘 Git-Test1

> **클라우드 기반 생성형 AI 활용 웹개발 실무 프로젝트** — Git 학습 및 실습 레포지토리

---

## 📌 프로젝트 개요

이 레포지토리는 Git의 핵심 개념과 명령어를 학습하고 실습하기 위해 만들어진 저장소입니다.  
버전 관리의 기초부터 브랜치 전략, 원격 저장소 연동까지 다양한 Git 워크플로우를 다룹니다.

---

## 🗂️ 목차

- [Git이란?](#-git이란)
- [SVN vs Git](#-svn-vs-git)
- [초기 설정](#-초기-설정)
- [파일 상태](#-파일-상태)
- [파일 등록 및 커밋](#-파일-등록--커밋)
- [커밋 이동 및 되돌리기](#-커밋-이동--되돌리기)
- [브랜치 관리](#-브랜치-관리)
- [Merge & Rebase](#-merge--rebase)
- [원격 저장소](#-원격-저장소)
- [충돌(Conflict) 대처](#-충돌conflict-대처)
- [고급 기능](#-고급-기능)
- [Git Ignore](#-git-ignore)
- [GUI 툴](#-gui-툴)
- [터미널 기본 명령어](#-터미널-기본-명령어)

---

## 🧩 Git이란?

- **버전 관리 / 형상 관리 시스템**
- SCM(Source Code Management)의 대표 도구
- 로컬과 원격 저장소를 모두 지원하여 오프라인 작업도 가능

---

## ⚖️ SVN vs Git

| 구분 | Git | SVN (Subversion) |
|------|-----|-----------------|
| 저장소 위치 | 로컬 + 원격 | 원격만 |
| 오프라인 작업 | ✅ 가능 | ❌ 불가능 |
| 속도 | 빠름 | 상대적으로 느림 |

---

## ⚙️ 초기 설정

```bash
# 사용자 이름 설정
git config --global user.name "사용자 이름"

# 사용자 이메일 설정
git config --global user.email "이메일 주소"

# 맥에서 한글 파일명 인식 문제 해결
git config --global core.precomposeunicode true

# 한글 깨짐 방지
git config --global core.quotepath false

# 설정 확인
git config --list

# 현재 폴더를 Git 로컬 저장소로 초기화
git init
```

---

## 📄 파일 상태

```bash
git status  # 현재 저장소의 상태 확인
```

| 상태 | 설명 |
|------|------|
| `Untracked` | 새로 생성되거나 Git이 추적하지 않는 파일 |
| `Unmodified` | 수정되지 않은 파일 |
| `Modified` | 수정된 파일 |
| `Staged` | `git add`로 스테이징된 파일 |

---

## 📦 파일 등록 & 커밋

```bash
# 특정 파일을 Staging Area에 추가
git add <파일명>

# 현재 폴더의 모든 파일 추가
git add -A
git add .

# 커밋 생성
git commit -m "커밋 메시지"

# add + commit 동시에 (Untracked 파일 없을 때만)
git commit -am "커밋 메시지"

# 커밋 내역 확인
git log
git log --oneline
git log --oneline --graph
```

---

## 🔄 커밋 이동 & 되돌리기

```bash
# 특정 커밋으로 이동 (커밋 ID 앞 7자리)
git checkout 6ef2a23

# 최신 커밋으로 이동
git checkout <branch_name>

# 해당 커밋으로 리셋 (이후 커밋 삭제)
git reset --hard 6ef2a23

# 특정 커밋만 되돌리기 (이력 유지)
git revert 6ef2a23
```

> ⚠️ `reset --hard`는 이후 커밋이 삭제되므로 주의하여 사용하세요.

---

## 🌿 브랜치 관리

```bash
# 브랜치 목록 확인
git branch

# 새 브랜치 생성
git branch <branch_name>

# 브랜치 전환
git checkout <branch_name>
git switch <branch_name>

# 새 브랜치 생성 + 전환
git switch -c <branch_name>

# 브랜치 삭제
git branch -d <branch_name>
```

---

## 🔀 Merge & Rebase

### Merge

```bash
git merge <branch_name>
```

| 방식 | 설명 |
|------|------|
| **Fast-forward** | main의 HEAD를 새 브랜치로 이동 (직선형 이력) |
| **3-way merge** | main과 branch 모두 변경된 경우 새 머지 커밋 생성 |

### Rebase

```bash
git rebase <branch_name>
```

> Fast-forward 형태로 이력을 정리하여 **커밋 그래프를 깔끔하게** 유지합니다.

---

## ☁️ 원격 저장소

```bash
# SSH 키 생성
ssh-keygen

# 원격 저장소 추가
git remote add origin https://github.com/.../.git

# 브랜치명 변경 (master → main)
git branch -M main

# 원격 저장소에 push
git push -u origin main

# 원격 저장소와 동기화
git pull

# 저장소 클론 (main 브랜치)
git clone <git주소>

# 특정 브랜치 클론
git clone -b <branch_name> <git주소>

# 원격 브랜치 포함 전체 브랜치 확인
git branch -a
```

---

## ⚡ 충돌(Conflict) 대처

Revert 또는 Merge 시 충돌이 발생하면 vim 편집기가 열립니다:

```
1. i 키 → Insert Mode 진입
2. 병합 메시지 입력
3. ESC 키 누르기
4. :wq 입력 후 Enter
```

---

## 🛠️ 고급 기능

| 기능 | 설명 |
|------|------|
| `fork` | 원본 저장소를 개인 원격 저장소로 복사 (Pull Request 가능) |
| `tag` | 특정 커밋에 버전 태그 부여 |
| `amend` | 마지막 커밋 내용 수정 |
| `cherry-pick` | 특정 커밋만 선택해 다른 브랜치에 적용 |
| `stash` | 변경사항을 임시 저장하고 나중에 꺼내기 |
| `fetch` | 원격 커밋을 가져오되 로컬에 반영하지 않음 |

---

## 🙈 Git Ignore

불필요한 파일을 Git 추적에서 제외합니다.

- 편의 사이트: [gitignore.io](https://www.toptal.com/developers/gitignore)
- `.gitignore` 파일에 무시할 파일/폴더 패턴을 작성

---

## 🖥️ GUI 툴

| 툴 | 설명 |
|----|------|
| [GitHub Desktop](https://desktop.github.com/) | GitHub 공식 GUI 클라이언트 |
| [Sourcetree](https://www.sourcetreeapp.com/) | Atlassian의 강력한 Git GUI 툴 |

---

## 💻 터미널 기본 명령어

| 명령어 | 설명 |
|--------|------|
| `pwd` | 현재 디렉토리 경로 확인 |
| `cd ~` | 홈 디렉토리로 이동 |
| `cd ..` | 상위 디렉토리로 이동 |
| `cd <디렉토리>` | 해당 디렉토리로 이동 |
| `ls -al` | 현재 디렉토리 파일 목록 확인 |
| `mkdir <이름>` | 새 디렉토리 생성 |
| `echo` | 터미널에 출력 또는 파일에 텍스트 작성 |

---

## 📚 참고 자료

- [공식 Git 문서](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [Pro Git Book (무료 전자책)](https://git-scm.com/book/ko/v2)
