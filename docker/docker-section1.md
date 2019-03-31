# docker 개요

## 왜 도커를 쓸까??

#### 일반적인 소프트웨어를 설치 및 실행 방법

1. 소프트웨어 다운로드
2. run install
3. install 도중 에러 메시지 발생
4. trobleshoot issue
5. rerun install
6. 다시 에러 메시지 발생
7. 4번으로 돌아가기


- 도커를 사용하면 위와 같은 상황이 발생하지 않는다.
- 도커를 사용하면 프로세스 설치와 실행이 매우 쉽다.(정확하게 도커를 통해 프로세스를 컨테이너화 하면..)

## 도커 란 무엇인가?
- Docker is platform or ecosystem around creating and running containers

## container란 무엇인가?
- 모든 프로세스를 실행하려면 운영체제의 커널이 필요하다
- 모든 명령은 system call을 통해 커널을 호출하고 커널은 CPU, MEMORY, Hard Disk, Network등을 컨트롤 한다. 
- A container is an instance of image
- container는 프로세스를 실행하기 위한 최소한의 패키지의 묶음이다.
- container를 사용하기 위한 핵심기술
    1. Namespacing
        - isolating resources per process(or group of processes
        - process, Hard drive, Network, Users, Hostnames, Inter Process communications
    2. control groups
        - Limit amount of resources used per process 
        - Memory, CPU Usage HD I/O, Network Bandwidth
- container의 핵심 기술인 namespacing, control groups은 linux 커널에서만 사용이 가능하다. 
- 그러면 어떻게 macos, 윈도우에서도 사용이 가능할까?
- docker를 사용하면 mac 또는 윈도우에서도 사용이 가능하다.
    - docker는 mac 또는 윈도우 위에 linux virtual machine을 실행하여 각 컨테이너들과 운영체제간에 연결고리 역할을 해준다. 

