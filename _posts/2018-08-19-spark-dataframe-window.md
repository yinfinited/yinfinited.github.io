
## window function 

Apache Spark 1.4 에 추가되었다.

Spark SQL에서 로우에 대해 값을 어떻게 반환하는지에 따라 두 가지 타입으로 나눈다.

1. 각 로우에 대해 하나의 값을 반환하는 경우
1. 여러 개의 로우에 대해 하나의 값을 반환하는 경우

전자로는 빌트인 함수들과 UDF가 있고 후자로는 합이나 최대값 등 집합함수가 있다.

하지만 랭크와 같이 여러 로우에 대해 계산하여 모든 로우에 대해 결과 값을 내야 하는 경우도 있다.




Window functions allow users of Spark SQL 
to calculate results such as 
  the rank of a given row or 
  a moving average over a range of input rows. 

window function 은 Spark SQL의 특정 범위의 row 에 대해 랭크나 이동평균을 구할 수 있다.

window function 은 expressiveness 를 매우 증가시켜준다.


