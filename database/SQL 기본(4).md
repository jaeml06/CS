### SQL 기본(4)



#### 명시적 형변환과 암시적 형변환

명시적 형변환은 형변환 함수를 사용해서 데이터 타입을 일치시키는 것으로 개발자가 SQL을 사용할 떄 형변환 함수를 사용해야 함.

##### 형변환 함수

- **TO_NUMBER (문자열)**

  문자열을 숫자로 변환

- **TO_CHAR (숫자 혹은 날짜, [FORMAT])**

  숫자 혹은 날짜를 지정된 FORMAT의 문자로 변환

- **TO_DATE (문자열, FORMAT)**

  문자열을 지정된 FORMAT의 날짜형으로 변환

암시적 형변환은 개발자가 형변환을 하지 않은 경우 데이터베이스 관리 시스템이 자동으로 형변환하는 것을 의미.



#### 내장형 함수

- **문자열 함수**
  - ASCII(문자) : 문자 혹은 숫자를 ASCII 코드값으로 변환
  - CHAR/CHAR(ASCII 코드값) : ASCII 코드값을 문자로 변환. 오라클 -> CHR, MYSQL -> CHAR
  - SUBSTR(문자열, m, n) : 문자열에서 m번째 위치로부터 n개를 자름
  - CONCAT(문자열1, 문자열2) : 문자열1과 문자열2을 결합
  - LOWER(문자열) : 영문자를 소문자로 변환
  - UPPER(문자열) : 영문자를 대문자로 변환
  - LENGTH 혹은 LEN(문자열) : 공백을 포함해서 문자열의 길이를 반환
  - LTRIM(문자열, 지정문자) : 왼쪽에서 지정된 문자를 삭제, 지정문자를 생략 시 공백 삭제
  - RTRIM(문자열, 지정문자) : 오른쪽에서 지정된 문자를 삭제, 지정문자를 생략 시 공백 삭제
  - TRIM(문자열, 지정문자) : 왼쪽 및 오른쪽에서 지정된 문자를 삭제, 지정문자를 생략 시 공백 삭제
- **날짜형 함수**
  - SYSDATE : 오늘의 날짜를 날짜 타입으로 알려줌
  - EXTRACT(YEAR FROM SYSDATE) : 날짜에서 년, 월, 일을 조회
- **숫자형 함수**
  - ABS(숫자) : 절댓값을 반환
  - SIGN(숫자) : 양수, 음수, 0을 구별
  - MOD(숫자1,  숫자2) : 숫자1을 숫자2로 나누어 나머지를 계산
  - CEIL/CEILING(숫자) : 숫자보다 크거나 같은 정수를 반환
  - FLOOR(숫자) : 숫자보다 작거나 같은 최대의 정수를 반환
  - ROUND(숫자, m) : 소수점 m 자리에서 반올림. m의 기본값은 0
  - TRUNC(숫자, m) : 소수점 m 자리에서 절삭. m의 기본값은 0



#### DECODE와 CASE문



- ##### DECODE

  비교문으로 EMPNO가 1000이면 TRUE를 응답하고 같지 않으면 FALSE를 응답

  > DECODE (EMPNO, 1000, 'TRUE', 'FALSE')

  

- **CASE**

  조건을 WHEN구에서 사용. 해당 조건이 참이면 THEN이 실행되고 거짓이면 ELSE구가 실행

  > CASE [expression]
  >
  > ​	WHEN condition_1 THEN result_1
  >
  > ​	WHEN condition_2 THEN result_2
  >
  > ...
  >
  > ​	WHEN condition_n THEN result_n
  >
  > END

#### ROWNUM