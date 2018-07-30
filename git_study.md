#GIT STUDY

----
#### git project 복사 및 git project push 및 pull 방법
----

- github project 복사(local과 project 연결)

```
 git clone git@github.com:nespot2/study-nespot2.git
```  

- git remote 명령으로 현재 프로젝트에 등록된 리모트 저장소를 확인할 수 있다.

```
 git clone -v
```

- SSH 공개키 만들기(git push를 사용하기 위해 ssh 공개키가 필요하다.)
- ssh-keygen 명령어를 사용하면 public key가 id_rsa.md 파일에 만들어 진다. (먼저 키를 어디에 저장할지 경로를(.ssh/id_rsa) 입력하고 암호를 두 번 입력한다. 이때 암호를 비워두면 키를 사용할 때 암호를 묻지 않는다. => 다 무시하고 그냥 엔터 입력)

```
cd ~/.ssh

ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/Users/schacon/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /Users/schacon/.ssh/id_rsa.
Your public key has been saved in /Users/schacon/.ssh/id_rsa.pub.
The key fingerprint is:
43:c5:5b:5f:b1:f1:50:43:ad:20:a6:92:6a:1f:9a:3a schacon@agadorlaptop.local
```
- id_rsa.pub 파일에 있는 ssh 공개키를 복사하여 github project에 ssh 공개키를 등록한다.
- settings => Deploy keys => Add deploy keys(project setting이 아닌 맨 상위에 있는 setting에 key를 deploy 해야한다.)
- 이제 local에 만들어진 file을 github project에 push가 가능해진다.


```
git push origin master
```

- github에있는 프로젝트를 pull할수도 있음

```
git pull oprigin master
```

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


