### SQL 기본(5)



#### ROWNUM

ROWNUM은 조회되는 행 수를 제한할 때 많이 사용됨

ROWNUM은 화면에 데이터를 출력할 떄 부여되는 논리적인 순번



#### ROWID

ORACLE 데이터베이스 내에서 데이터를 구분할 수 있는 유일한 값

ROWID룰 통해서 데이터가 어떤 데이터 파일, 어느 블록에 저장되어 알 수 있음

| 구조           | 길이  | 설명                                                         |
| -------------- | ----- | ------------------------------------------------------------ |
| 오브젝트 번호  | 1~6   | 오브젝트 별로 유일한 값을 가지고 있으며, 해당 오브젝트가 속해 있는 값 |
| 상대 파일 번호 | 7~9   | 테이블스페이스에 속해 있는 데이터 파일에 대한 상대 파일번호  |
| 블록 번호      | 10~15 | 데이터 파일 내부에서 어느 블록에 데이터가 있는지 알려줌      |
| 데이터 번호    | 16~18 | 데이터 블록에 데이터가 저장되어 있는 순서를 의미             |



#### WITH

서브쿼리를 사용해서 임시 테이블이나 뷰처럼 사용할 수 있는 구문

서브 쿼리 블록에 별칭을 지정할 수 있음



#### DCL

- **GRANT**

  데이터베이스 사용자에게 권한을 부여

  데이터베이스 사요을 위해서 권한이 필요하며 연결, 입력, 수정, 삭제, 조회

  >GRANT privileges ON object TO user;
  >
  >
  >
  >privileges는 권한을 의미하며 object 테이블명
  >
  >user는 Oracle 데이터베이스 사용자를 지정하면 됨.

  Privileges

  - SELECT
  - INSERT
  - UPDATE
  - DELETE
  - PEFERENCES : 제약조건을 생성하는 권한을 부여
  - ALTER : 수정할 수 있는 권한을 부여
  - INDEX : 인덱스를 생성할 수 있는 권한을 부여
  - ALL : 테이블에 대한 모든 권한을 부여

  

  WITH GRANT OPTION과 ADMIN OPTION

  - WITH GRANT OPTION

    특정 사용자에게 권한을 부여할 수 있는 권한을 부여

    권한 A 사용자가 B에 부여하고 B가 다시 C를 부여한 후에 권한을 취소하면 모든 권한이 회수됨

  - WITH ADMIN OPTION

    테이블에 대한 모든 권한을 부여

    권한을 A 사용자가 B에 부여하고 B가 다시 C에 부여한 후에 권한을 취소하면 B사용자 권한만 취소됨

- **REVOKE**

  데이터베이스 사용자에게 부여된 권한을 회수

  > REVOKE privileges ON object FROM user;



#### TCL

- ##### commit

  INSERT, UPDATE, DELETE문으로 변경한 데이터를 데이터베이스에 반영

  변경 이전 데이터는 잃어버림

  commit이 완료되면 데이터베이스 변경으로 인한 LOCK이 해제됨

  commit을 실행하면 하나의 트랜잭션 과정을 종료

- ROLLBACK

  데이터에 대한 변경 사용을 모두 취소하고 트랜잭션을 종료

  ROLLBACK을 실행하면 LOCK이 해제되고 다른 사용자도 데이터베이스 행을 조작 할 수 있음

- SAVEPOINT

  트랜잭션을 작게 분할하여 관리하는 것으로 SAVEPOINT를 사용하면 지정된 이후의 트랜잭션만 ROLLBACK 할 수 있음

  SAVEPOINT의 지정은 SAVEPOINT <SAVEPOINT명>을 실행

  지정된 SAVEPOINT까지만 데이터 변경을 취소하고 싶은 경우는  "ROLLBACK TO <SAVEPOINT>" 을 실행  

  