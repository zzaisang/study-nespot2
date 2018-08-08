# GIT STUDY

----
## git project 복사 및 git project push 및 pull 방법
----

- github project 복사(local과 project 연결)

```
 git clone https://github.com/nespot2/study-nespot2.git
```  

- SSH 공개키 만들기(git push를 사용하기 위해 ssh 공개키가 필요하다.)
- ssh-keygen 명령어를 사용하면 public key가 ./ssh에 id_rsa.md 파일이 만들어 진다. 
- cd ~/.ssh, ssh-keygen

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

## git 구조
----
git 구조
- tract file(add, modified, commit 파일), untract file(그외)
- untracked(working directory), stage(add 영역), modified, unmodified(commit 영역)

![git 구조](https://git-scm.com/book/en/v2/images/lifecycle.png)

## git 기본 명령어
----

- ./git => repository
- git init
- git add
- git commit -a(무조껀 commit한다.)m(메시지)
- git show
- git log
- git ls-files

- git reset HEAD 파일명 => add된 파일을 reset한다
- git checkout -- README.md => modified한 파일을 reset 한다.

## 로그 히스토리 및 얼라이어스를 이용한 새로운 명령어
----

- git log --oneline --graph --decorate --all
- git config --global alias.hist "log --oneline --graph --decorate --all"
- git hist -- "로그를 확인하고 싶은 파일"

## 파일명 변경 및 파일 삭제
----

- git mv "변경 대상이 되는 파일명" "내가 변경할 파일명" => 그다음 commit
- git rm "삭제할 파일명" => 그다음 commit

## git 바깥에 있는 파일들 관리
----
- git add -A => untract 파일 및 변경 삭제 파일 등등 모두 staged에 올려버린다.
- git add -u => not staged인 파일만 staged로 바꿔버림.

## git remote
----

- GitHub에 빈 Remote Repository를 생성한 후 git remote를 이용하여 Local Repository와 연결할 수 있습니다. 다음과 같은 명령을 이용합니다.

```
git remote add origin “Remote Repository URL”
```

- 연결이 성공했는지를 다음의 명령어를 이용해서 확인해 볼 수 있습니다.

```
git remote -v
```

