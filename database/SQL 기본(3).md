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



#### where문 사용

- 비교 연산자
  - =
  - <, >
  - <=, >=
- 부정 비교 연산자
  - !=
  - ^=
  - <>
  - NOT 칼럼명 =
  - NOt 칼럼명 >
- 논리 연산자
  - and
  - or
  - not
- SQL 연산자
  - LIKE '%비교 문자열%'
  - between a and b
  - in
  - is null
- 부정 SQL 연산자
  - not between a and b
  - not in (list)
  - is not null

##### NULL 관련 함수

- NVL 함수 : NULL이면 다른 값으로 바꾸는 함수. 'NVL(MGR, 0)'은 MGR칼럼이 NULL이면 0으로 바꿈
- NVL2 함수 : 'NVL2(MGR, 1, 0)'은 MGR칼럼이 NULL이 아니면 1을, .NULL이면 0을 반환
- NULLIF 함수 : 'NULLIF(exp1, exp2)'은 exp1과 exp2가 같으면 NULL을, 같지 않으면 exp1을 반환
- COALESCE : 'COALESCE(exp1, exp2, exp3, ...)'은 epx1이 NULL이 아니면, exp1의 값을, 그렇지 않으면 그 뒤의 값의 NULL 여부를 판단하여 값을 반환



#### GROUP 연산

테이블에서 소규모 행을 그룹화하여 합계, 평균, 최댓값, 최소값 등을 계산 가능.

having구에 조건문을 사용

- ##### 집계 함수 종류

  - count() : 행 수를 조사
  - sum() : 합계를 계산
  - avg() : 평균을 계산
  - max()와 min() : 초댓값과 최솟값을 계산
  - stddev() : 표준편차를 계산
  - variance () : 분산을 계산