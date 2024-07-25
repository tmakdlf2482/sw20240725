# git&github

- git init 명령어 : 작업 폴더에서 git 쓰고 싶을 때 (repository 저장소 생성)

파일을 기록(버전생성)

- git add 명령어 : 파일 현재상태를 기록(버전 생성)
- git commit -m ‘메모하고싶은내용’

파일을 기록(버전생성) 정리

1. git add로 기록할 파일 고르기
2. 고른파일 기록명령은 git commit (commit은 일종의 저장소에 옮기는 것)

※ [작업 폴더(여러 소스 파일 존재)] → git add → [staging area] → git commit → [repository(저장소)]

※ staging 한다 : 작업 폴더(여러 소스 파일)에서 staging area로 파일을 고르는 행위

- 여러 파일 staging하려면 → git add 파일1 파일2 …
- 모든 파일 staging하려면 → git add .
- 상태창 열기 → git status
- commit 내역 조회 → git log —all —oneline
- commit 내역 조회2 → git log —all —oneline —graph (HEAD는 현재 나의 위치)

- 최근 commit vs 현재파일 차이점 보여줌(잘 안씀) → git diff, 이때 j키, k키로 스크롤 이동, 끝내고 싶을때는 q키
- git diff보다 “git difftool”을 더 자주 사용, git difftool은 에디터인데 h, j, k, l키가 방향키 / 종료는 :q 또는 :qa
- git difftool 커밋아이디 : 현재파일 vs 특정커밋 비교가능, 커밋아이디는 git log —all —oneline 했을 때 첫번째로 나오는 노란색 글씨
- git difftool 커밋아이디1 커밋아이디2 : 커밋아이디1 과 커밋아이디2를 비교

- git branch 브랜치명 : 브랜치명으로 브랜치 생성
- git switch 브랜치명 : 해당 브랜치명으로 이동

- branch를 합치는 것 → merge(병합)
- branch 합치는 순서 : 기준이 되는 branch로 이동 → [git merge 합칠브랜치명] 명령어
- 충돌 해결은 코드고치고 git add & git commit -m ‘메시지내용’

- merge 완료된 branch 삭제 : git branch -d 브랜치명
- merge 안한 브랜치 삭제 : git branch -D 브랜치명

- rebase & merge 하고 싶을 때 :  “새로운 브랜치”로 이동 → git rebase 중심브랜치명 → 중심브랜치로 이동 → git merge 새로운브랜치명

- main 브랜치의 로그 출력하면 쓸데없는 branch 로그 안나오게 하기 : git merge —squash 새브랜치

- git restore 파일이름 : 파일 복구
- git restore —source 커밋아이디 파일명 : 특정 commit 시점으로 파일 복구하는 법
- git revert 커밋아이디 : 해당 커밋아이디에서 작업한거 제거하는 commit 생성(commit 취소)
- git revert 커밋아이디1 커밋아이디2 : commit 여러개 취소가능
- git revert HEAD : 최근 commit 취소가능

- git reset —hard 커밋아이디 : 과거로 모든걸 되돌리기
- git reset —soft 커밋아이디 : 리셋인데 변동사항 지우지 말고 스테이징해놓기
- git reset —mixed 커밋아이디 : 리셋인데 변동사항 지우지 말고 unstage 해놓기

★ git push -u 원격저장소주소 올릴로컬브랜치명 : 로컬 → 원격저장소 업로드 (이때, 원격저장소주소가 너무 긴데, 이것을 해결하기 위해 git에서 변수문법 사용할 수 있음, git remote add “변수명” 원격저장소주소)

git clone 원격저장소주소 : 원격저장소 복제

git pull 원격저장소주소 브랜치명 : 원격저장소 → 로컬저장소

git pull = git fetch + git merge

git fetch : 원격저장소 신규 commit 가져오기

git merge : 내 브랜치에 merge

★ git push 하기전에 git pull 부터 하자!!

★ 다수의 개발자들이 1개의 프로젝트를 개발할 때, 각각 브랜치를 만들어서 개발하고 merge하는게 안정적

git stash : 임시로 잠깐 코드 보관하고 싶을 때 사용 (최근 commit과의 차이점을 전부 보관해줌), staging 안해놓은 새로운 파일은 stash 안될수도 있음

git stash list : 보관된 코드 목록 조회

git stash save ‘메모‘ : 임시로 코드를 잠깐 보관할 때 메모도 함께 하고싶을 때 사용

git stash pop : 임시로 잠깐 보관된 코드 불러오기 (가장 최근것부터 불러옴)

git stash drop 번호 : stash 1개 삭제

git stash clear : stash 전부 삭제