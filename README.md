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
```ruby
select restaurant_name, customer_id
from food_orders
where food_preparation_time between 20 and 30 and cuisine_type='Korean'
```
food_orders 테이블에서 select를 통해 고객번호와 식당명이 표시되도록하고 where절을 사용해 food_preparation_time이 20~30분 내이고 cuisine_type이 Korean인 조건만 필터링.
## SQL 2주차 내용정리 
데이터를 group by 를 통해 범주별로 계산하고 order by를 통해 데이터를 정렬한다. 
### 2주차 문제
### 음식 종류별 가장 높은 주문 금액과 가장 낮은 주문금액을 조회하고, 가장 낮은 주문금액 순으로 (내림차순) 정렬하기
```ruby
select cuisine_type,
       min(price) min_price,
       max(price) max_price
from food_orders
group by cuisine_type
order by min(price) desc
```
food_orders 테이블에서 select를 통해 cuisine_type과 가장 낮은 주문금액과 가장 높은 주문 금액을 조회하고 group by 를 통해 cuisine_type을 범주로 정하고 order by로 정렬한다.
## SQL 3주차 내용정리
특정문자를 다른문자로 변경(replace), 원하는 문자만 추출(substr), 여러칼럼의 문자를 합치기(concat), 원하는 조건에 충족하는 경우와 불충족하는 경우 지정(if,case(여러조건  지정 가능))
### 3주차 문제
### 다음의 조건으로 배달시간이 늦었는지 판단하는 값을 만들어주세요. 
- 주중 : 25분 이상
- 주말 : 30분 이상
```ruby
select order_id,  
       restaurant_name,
       day_of_the_week,
       delivery_time,
       case when day_of_the_week='Weekday' and delivery_time>=25 then 'Late'
            when day_of_the_week='Weekend' and delivery_time>=30 then 'Late'
            else 'On-time' end "지연여부"
from food_orders
```
첫번째로 배달시간, 고객번호, 주중/주말여부, 음식점명 을 칼럼으로 표시하고 주중에 배달시간이 25분 이상이면 늦음,주말에 배달시간이 30분 이상이면 늦음으로 지정후 이외의 경우 정시 도착 으로 지연여부를 표시.

