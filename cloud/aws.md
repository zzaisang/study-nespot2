# Amazon Web Service
----

- 회원가입
	- 신용카드 및 check 카드 등록 => 서버를 사용한 만큼 카드에서 돈이 지불됨
	- 나머지는 하라는 대로 하면됨
	- 회원가입이 완료되면 1달러 요금이 청구됩니다. => 실제 요금을 청구하는 것이 아닌 이 카드가 유효한 카드인지 확인하기 위한 절차입니다. => 3~5일 내에 해당 청구 건은 사라집니다.
	- id가 해킹당하면 요금 폭탄을 맞을 수 있습니다. aws iam에 접속하면 보안 상태를 확인 할수 있습니다. 총 5단계가 있으면 5단계 다 충족하는 것이 보안에 좋습니다.
		- 저는 2단계를 충족하였습니다.(루트 액세스 키 삭제, 루트 계정에 MFA 활성화)
	
- aws 요금정책
	- 여러 요금 정책 존재
	- aws 프리티어는 1년동안 무료로 aws 서비스를 사용할 수 있습니다.


- region 
[아마존 웹서비스 지역별 지연시간 측정](http://www.cloudping.info/)

- avaliabilty zone(가용구역)
	- 같은 지역끼리 데이터를 빠르게 주고 받습니다..(전용선)
	- 다른 지역끼리는 데이터를 느리게 주고 받습니다.(인터넷으로 연결되어 있음.)
	
	
### AWS EC2
----
- EC2(Elastic Compute Cloud)는 독립된 컴퓨터를 임대해주는 서비스입니다. 
- EC2 생성방법
	- AMI 선택(aws linux 2 선택)
	- 모든 인스턴스 유형(t2.micro 선택 => 프리 티어 사용가능)
	- 인스턴스 서버 구성
	- 스토리지 추가
	- 태크 추가
	- 보안 그룹 구성(ip 제한을 줄 수 있다.)
	- 검토 => luanch 버튼을 누르면 비밀번호 파일을 생성합니다. => 해당 비밀번호로 instance 접근 가능합니다.
	
- EC 접근 방법(mac os)
	- open terminal
	- 비밀번호 파일이 있는 디렉토리로 이동
	- 비밀번호 파일 권한이 400이 아니면 옆과 같은 명령어 실행 => chmod 400 파일명.pem
	- ssh -i "webpwd.pem" ec2-user@ec2-13-125-83-42.ap-northeast-2.compute.amazonaws.com => 접속
	
- java jdk-8 설치

```
sudo yum install -y java-1.8.0-openjdk-devel.x86_64
```

	
	
