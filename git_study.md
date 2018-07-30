#GIT STUDY

----

#### git 구조
----
git 구조
- tract file(add, modified, commit 파일), untract file(그외)
- working directory, stage(add 영역), repository(commit 영역)

#### git 기본 명령어
----

./git => repository
git init
git add
git commit -a(무조껀 commit한다.)m(메시지)
git show
git log
git ls-files

git reset HEAD 파일명 => add된 파일을 reset한다
git checkout -- README.md => modified한 파일을 reset 한다.

#####로그 히스토리 및 얼라이어스를 이용한 새로운 명령어
----

git log --oneline --graph --decorate --all
git config --global alias.hist "log --oneline --graph --decorate --all"
git hist -- "로그를 확인하고 싶은 파일"

#####파일명 변경 및 파일 삭제
----

git mv "변경 대상이 되는 파일명" "내가 변경할 파일명" => 그다음 commit
git rm "삭제할 파일명" => 그다음 commit

#### git 바깥에 있는 파일들 관리
git add -A => untract 파일 및 변경 삭제 파일 등등 모두 staged에 올려버린다.
git add -u => not staged인 파일만 staged도 바꿔버림.


