# 11/28 TIL
## SQL 입문 
11/25일에 시작한 데이터분석가 부트캠프에 늦게합류되어 오늘처음으로 SQL을 입문하였다.
시간이 조금 걸리긴 했지만 3주차 까지 학습하였다.
## SQL이란?
SQL은 DB와 대화하는 언어로 입력과 출력을 질의과정으로 표현한다.
따라서 Query(질의)작성을 통해 DB에 필요한 데이터를 요청한다.

데이터베이스는 엑셀파일과 같이 여러 정보를 수집한 테이블들을 가지고 있는데
그 테이블의 각 열을 컬럼 또는 필드라고 부르고 그속에서 원하는 정보를 추출하기 위해 Query를 작성한다.

## SQL 1주차 내용정리
DB에서 원하는 칼럼과 테이블을 select 와 from을 통해 요청한 후 필요한 조건에 맞춰 where절을 사용하여 필터링 한다
## 1주차 문제
#### 상품준비시간이 20~30분 사이인, 한국음식점의식당명과 고객번호 조회하기 
*select* restaurant_name, customer_id

*from* food_orders

*where* food_preparation_time between 20 and 30 and cuisine_type='Korean'

