### SQL 활용(1)



#### 조인(join)

- **EQUI(등가) JOIN**

  조인은 여러 개의 릴레이션을 사용해서 새로운 릴레이션을 만드는 과정

  조인의 가장 기본은 교집합을 만드는 것

- **INNER JOIN**

  INNER JOIN구에 두 개의 테이블명을 서술하고 ON문 조인 조건을 서술함

  > ex) EMP INNER JOIN DEPT ON EMP.DEPTNO = EMP.DEPTNO

- **INTERSECT 연산**

  두 개의 테이블에서 교집합을 조회

- **Non - EQUI(비등가) JOIN**

  Non - EQUI는 두 개의 테이블 간에 조인하는 경우 "="을 사용하지 않고 ">", "<", ">=", "<="등 사용

- **OUTER JOIN**

  OUTER JOIN은 두 개의 테이블 간에 교집합을 조회하고  한쪽 테이블에만 있는 데이터도 포함시켜서 조회

  - LEFT OUTER JOIN

    두 개의 테이블에서 같은 것을 조회하고 왼쪽 테이블에만 있는 것을 조회

  - RIGHT OUTER JOIN

    두 개의 테이블에서 같은 것을 조회하고 오른쪽 테이블에만 있는 것을 포함해서 조회

- **CROSS JOIN**

  조인 조건구 없이 2개의 테이블을 하나로 조인

  조인구가 없기 때문에 카테시안 곱이 발생

- **UNION을 사용한 합집합 구현**

  - UNION

    2개의 테이블을 하나로 합히는 것 이때, 두 개의 테이블의 칼럼 수, 칼럼의 데이터 형식 모두 일치해야 함

    2개의 테이블을 하나로 합치면서 중복된 데이터를 제거

    정렬 과정을 발생

  - UNION ALL

    2개의 테이블을 하나로 합치는 것.

    중복을 제거하거나 정렬을 유발하지 않음

- **차집합을 만드는 MINUS**

  두 개의 테이블에서 차집합을 조회

  먼저 쓴 SELECT문에는 있고 뒤에 쓰는 SELECT문에는 없는 집합을 조회하는 것

  #### 계층형 조회

계층형 조회는 Oracle 데이터베이스에서 지원하는 것으로 계층형으로 데이터를 조회 가능

CONNECT BY 형태의 구조로 질의를 수행하는 것으로 START WITH구는 시작 조건을 의미하고 

CONNECT BY PRIOR는 조인 조건. Root 노드로부터 하위 노드의 질의를 실행

- **CONNECT BY 키워드**
- LEVEL : 검색 항목의 깊이를 의미
  
- CONNECT_BY_ROOT : 계층 구조에서 가장 최상위 값을 표시
  
- CONNECT_BY_ISLEAF : 계층 구조에서 가장 최하위를 표시
  
- SYS_CONNECT_BY_PATH : 계층 구조의 전체 전개 경로를 표시
  
- NOCYCLE : 순환 구조가 발생지점까지만 전개
  
- CONNECT_BY_ISCYCLE : 순환 구조 발생 지점을 표시

- **계층형 조회**
  - START WITH 키워드 : 계층 전개의 시작 위치를 지정하는 것
  - PRIOR 자식 = 부모 : 부모에서 자식 방향으로 검색을 수행하는 순방향 전개
  - PRIOR 부모 = 자식 : 자식에서 부모방향으로 검색을 수행하는 역방향 전개
  - NOCYCLE : 데이터를 전개하면서 이미 조회된 데이터를 다시 조회되면 CYCLE이 형성됨
  - Order siblings by 칼럼명 : 동일한 LEVEL인 형제노드 사이에서 정렬을 수행

​    