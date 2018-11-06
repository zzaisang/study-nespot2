# Mariadb


- Mariadb 시작 및 종료 
	- mysql.server start
	- mysql.server stop

- mariadb 계정접속
    - Mysql -u nespot2 -p nice
    - 패스워드 입력
    - Then can access nice db on mariadb

-  db 생성방법
    - Create database nice
    - Nice db 생성됨
- mariadb 계정 생성방법
	- create user ‘nespot2’@‘localhost’ identified by ‘zaq1234!’;
	- Nespot2 계정생성

- 권한부여
    - grant all privileges on nice.* to nespot2@‘localhost’;

- 컬럼 확인방법
	- SHOW COLUMNS FROM mytable FROM mydb;
	- SHOW COLUMNS FROM mydb.mytable;

- Maria db 패스워드 변경
	- mysql -uroot mysql
	- update user set password=password('변경할비밀번호') where user='root';
	- flush privileges;
	- exit;
	
	
- mariadb db export (dump)

```sql
mysqldump -u{계정} --port={port} --host={host} -p{password} {database_name} > data-dump.sql
```

- {host} jdbc:mariadb는 제거한다.

- mariadb db import (dump)

```sql
mysql -u{계정} -p{password} {database_name} < data-dump.sql

```

- table 컬럼 삭제

```sql
ALTER TABLE {TABLE 명} DROP {컬럼 명}
```

- table 컬럼 변경

```sql
ALTER TABLE [테이블명] MODIFY [컬럼이름] [새컬럼타입];
ALTER TABLE [테이블명] CHANGE [컬럼이름] [새컬럼이름] [새컬럼타입];
```

- table 컬럼 추가

```sql

마지막에 추가 : ALTER TABLE [테이블명] ADD COLUMN [컬럼이름] [컬럼타입];
지정 컬럼 뒤에 추가 : ALTER TABLE [테이블명]  ADD COLUMN [컬럼이름] [컬럼타입] AFTER [컬럼이름];
제일 앞에 추가 : ALTER TABLE [테이블명] ADD COLUMN [컬럼이름] [컬럼타입] FIRST;
```

- 인덱스에 새항목 추가

```sql
ALTER TABLE [테이블명] ADD INDEX([컬럼이름])
```

- 인덱스 삭제

```sql
ALTER TABLE [테이블명] DROP INDEX [컬럼이름]
DROP INDEX [인덱스이름] ON [테이블명]
```

- 기본키(Primary Key or PK) 지정하기

```sql
ALTER TABLE [테이블명] ADD PRIMARY KEY([컬럼이름]);
```


- 기본키(Primary Key or PK) 삭제하기

```sql
ALTER TABLE [테이블명] DROP PRIMARY KEY;
```

- 자동 증가 값 초기화 하기

```sql
ALTER TABLE [테이블명] AUTO_INCREMENT=[a];        // a값에는 시작하고 싶은 정수를 입력하면 됨
```

