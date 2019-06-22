# 2019년 6월 22일

- 오늘 할일

1. AWS RDS 서버 셋팅
    - vpc는 public으로 설정한다.
    - 단순하게 방화벽에서 접근을 제어한다.
    - 파라메터 그룹을 생성하고 charset을 utf-8로 한다.
        - 파라메터 그룹 생성
        - character 검색
        - utf-8로 변경
        - collation 검색
        - utf8_general_ci로 변경
        - db 인스턴스 수정에서 파라메터 그룹 변경
        - charset 설정 완료 후 database를 만들어야 database도 character set이 적용된다.(명심 또 명심)
        - server에서 수동 변경 가능
            - [mariadb 문서](https://mariadb.com/kb/en/library/setting-character-sets-and-collations/#server-level)
    - 나중에는 vpc를 private으로 설정 하고 vpc끼리 통신하게 수정할 예정이다.

2. spring jpa를 이용한 db 접근
    - country_code db에 데이터 저장
    
3. python selenium을 이용한 크롬드라이버 연동

