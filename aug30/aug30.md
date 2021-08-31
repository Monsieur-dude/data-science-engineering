# DBMS, SQL     
* Data Base Management System
    * 데이터 저장
    * 데이터 검색
    * 중복데이터가 많음 -> 저장공간낭비
    * 따라서 RDBMS 나옴
    * RDBMS(relational database management system)
        * 테이블 관계형 
        * DB 생성
        * table 생성
        * table 관계 설정
    * DB/DBMS 특징
        * 데이터 무결성
            * DB 속 데이터는 오류가 없어야 함
            * 제약조건(constraint)의 특성을 갖음 -> 데이터를 넣는 정확한 룰이 있ㅇ
        * 데이터 독립성 : DB 크기나 저장소를 변경해도 기존에 작성된 응용프로그램에 영향을 주지 않아야 함
        * 보안 : 접근할 수 있는 사람이 제한적
        * 데이터 중복 최소화
        * 응용 프로그램 제작, 수정이 쉬워야함
        * 데이터 안정성 향상
    * 데이터베이스 모델링, 용어
        * 데이터 : 정보만 존재, 체계화 X
        * 테이블 : 데이터를 표 형태로 입력
        * 데이터베이스 : 테이블을 저장하는 저장소, 각 DB는 고유명을 가짐
        * DBMS : DB관리하는 소프트웨어 
        * Column, row
        * primary key : 각 테이블당 하나만 지정, 중복 X, 공백 X 
        * foreign key : 두 테이블의 관계를 이어주는 키 
        * DDL (data definition language)
            * create : 계정, 테이블 생성
            * alter : 수정
            * drop : 테이블 전체를 삭제
        * DML (data manipulation language)
            * insert : 삽입
            * upate : 업데이트
            * delete : 테이블 내 데이터만 삭제
        * DCL (data control language)
            * grant : 부여
            * revoke : 회수
            * deny : 거절
* SQL(structured query language)
    * view : 가상의 테이블, 실제 데이터 X
    * stored procedure : SQL 문을 묶어서 함수같은 역할을 함
    * trigger : insert, update 또는 Delete 작업을 실행 시 작업이 실했됐음을 알리는 명령어
    * 문법, 기본
        * `--` 한 줄로 된 주석
        * `/*` `*/` 블록을 주석
        * `USE` databaseName;
        * `SHOW` databases;
        * `SELECT` database() : 현재 사용중인 DB 출력
        * `SELECT` columnName;
            1. `FROM` tableName
            2. `WHERE` condition
                * `BETWEEN` number1 `AND` number2;
                * `IN` (data1, data2, ...);
                * `LIKE` text`%`;
                    * `%` : 글자수를 포함 X
                    * `-` : 글자수를 포함 O
                * SubQuery 
                    * query 의 where 와 subquerydml select 는 같아야 함, 괄호로 감싸줘야 함
                    * ANY, ALL, SOME
                    * ex) select * from table where height > `(select height from table where name = 'James')`;
            3. `GROUP BY` {columnName | expr | position}
                * `sum`(columnName)
                * `avg`()
                * `max`()
                * `count`()
                * `count`(`distinct`) : 중복데이터 제외
                * `stdev`() : 표준편차
                * `var_samp`() : 분산
                * `WITH ROLLUP` : 중간합계를 계산
            4. `HAVING` where_condition 
                * GROUP BY에 쓰인 집계함수에 대해서 조건을 제한함
            5. `ORDER BY` {columnName | expr | position}
                * 출력 순서만 바꿔주는 구문
                * 기본적으로 asc(ascending) 정렬, 내림차순을 원하면 columnName 뒤에 desc(descending)
                * `DISTINCT` 중복 데이터는 1번만 출력
                * `LIMIT` n1, n2 : n1 번째 데이터에서 n2개만큼 출력
        * `CREATE TABLE` tableName (SELECT columns from tableName) 
        * `DROP TABLE` tableName; : 테이블를 삭제
        * `INSERT` [INTO] tableName[(col1, col2, ...)] VALUES (data1, data2 ...)
            * `AUTO_INCREMENT` 자동으로 증가하는 값 입력함
        * `UPDATE` tableName `SET` col1 = data1, col2 = data2,... `WHERE` condition;
        * `DELETE` `FROM` tableName `WHERE` condition; 
        
