Git
- 버전관리, 형상관리
- SCM(Source Code Management)

SVN(Subversion) vs Git
- Git: 로컬, 원격 둘 다 저장소를 따로 둠
- SVN: 원격에만 저장소를 둠 (인터넷 서버가 안되면 먹통)

초기 명령어
- 사용자 이름 설정 : git config --global user.name "사용자 이름"
- 사용자 이메일 설정 : git config --global user.email "이메일 주소"
- 맥사용시 파일명이 한글일경우 인식문제 해결 : git config --global core.precomposeunicode true
- git에서 한글 깨짐이 발생하는 경우 : git config --global core.quotepath false
- config 내용 확인 : git config --list
- 현재 폴더를 Git 로컬 저장소로 생성 : git init

파일의 상태
- 현재 저장소의 상태 확인 : git status
    - Untracked : 파일 생성, 삭제시 변동
    - Unmodified : 수정하지 않은 파일
    - Modified : 수정된 파일
    - Staged : git add로 등록한 파일

파일등록
- 특정 파일을 staging area에 추가 : git add "파일명"
- 현재 폴더의 모든 파일 추가 : git add -A / git add .

커밋 Commit
- 저장소의 변경 내용을 특정 시점(branch)에 저장하는 행위
- 또는 저장된 덩어리를 의미하는 말
- 현재 폴더의 변경사항을 확인 : git status
- 현재 상태에서 커밋 생성 : git commit -m "commit message"
- add와 commit을 동시에 : git commit -am "commit message" (Untracked상태 파일이 없을 때만)
- 현재 저장소의 커밋 내역을 확인 : git log / git log --oneline / git log --oneline --graph

Commit간 이동
- 원하는 커밋으로 이동 : git checkout 6ef2a23(commit id 앞7자리)
- 최신 커밋으로 이동 : git checkout branch_name

Commit 되돌리기
- 해당 id의 커밋으로 되돌림 해당 커밋이후의 커밋은 삭제됨 : git reset --hard 6ef2a23
- 해당 id의 커밋만 지우고 나머지의 커밋을 이어서 유지 : git revert 6ef2a23

Branch
- branch 목록 확인 : git branch
- 새로운 branch 생성 : git branch branch_name
- 작업 branch 변경 : git checkout branch_name / git switch branch_name
- 새로운 branch를 생성하고 변경 : git switch -c branch_name
- branch 삭제 : git branch -d branch_name

Merge
- 현재 branch에 특정 branch merge : git merge branch_name
- fast-forward merge : main의 head를 새로운 branch로 옮기는 방법
- 3-way merge : 각각 main과 branch에 변화가 생겨서 둘을 merge하는 방법

Rebase
- 현재 branch에 특정 branch merge : git rebase branch_name
- fast-forward merge 모양으로 merge함 (그래프가 간결해짐)

원격 저장소 생성
- ssh key 생성 : ssh-keygen
- 새로운 원격저장소를 origin이름으로 추가 : git remote add origin https://github.com... .git
- master branch명을 main으로 변경 : git branch -M main
- origin 원격저장소의 main branch에 push : git push origin main
- 원격저장소와 local의 상태를 일치시킴 : git pull

기타 터미널 명령어
- pwd : 현재 디렉토리 확인
- cd ~ : 홈 이동
- cd (디렉토리) : 디렉토리 이동
- ls -al : 현재 디렉토리 내 파일 리스트 확인
- mkdir : 새 디렉토리(폴더) 생성

Revert, Merge할 때 Conflict 상황 대처
- 메세지를 남기라고 뜰 때:
    - i키 누르기 (insert Mode로 변경)
    - 병합 메세지 입력
    - esc키 누르기
    - :wq 입력
    - enter키 누르기

