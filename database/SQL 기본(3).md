### SQL 기본(3)



#### DML



##### insert문

> **insert into** table (column1, column2) **values** (expression1 ,expression2);

- 데이터를 입력할 때 문자열을 입력하는 경우에는 '' 를 사용해야 함.

- 만약 특정 테이블의 모든 칼럼에 대한 데이터를 삽입하는 경우에는 칼럼명 생략 가능
- 모든 칼럼에 데이터를 입력



##### update문

> update EMP
>
> ​		set ename = '조조'
>
> ​		where empno = 100;

- 입력된 데이터의 값을 수정하려면, update문을 사용함.
- 만약, update문에 조건문을 입력하지 않으면 모든 데이터가 수정됨





##### delete문

> delete from EMP
>
> ​		where empno = 100;

- 원하는 조건을 검색해서 해당되는 행을 삭제
- delete문으로 데이터를 삭제한다고 해서 테이블의 용량이 초기화되지 않음
- truncate table 테이블 명; : 테이블의 모든 데이터를 삭제, 데이터가 삭제되면 테이블 용량은 초기화



##### select문 사용

> select * 
>
> from EMP
>
> where 사원번호 = 1000;



##### select