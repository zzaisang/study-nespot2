# Mariadb


- Mariadb 시작 및 종료 
	1. mysql.server start
	2. mysql.server stop

- mariadb 계정접속
    1. Mysql -u nespot2 -p nice
    2. 패스워드 입력
    3. Then can access nice db on mariadb

-  db 생성방법
    1. Create database nice
    2. Nice db 생성됨
- mariadb 계정 생성방법
	1. create user ‘nespot2’@‘localhost’ identified by ‘zaq1234!’;
	2.  Nespot2 계정생성

- 권한부여
    1. grant all privileges on nice.* to nespot2@‘localhost’;

- 컬럼 확인방법
	1. SHOW COLUMNS FROM mytable FROM mydb;
	2. SHOW COLUMNS FROM mydb.mytable;

- Maria db 패스워드 변경
	- mysql -uroot mysql
	- update user set password=password('변경할비밀번호') where user='root';
	- flush privileges;
	- exit;