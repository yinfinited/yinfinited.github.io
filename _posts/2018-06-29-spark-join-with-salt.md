---
layout: post
title: "Salted Join"
author: "yinfinited"
categories: 'dev'
tags: ['spark']
typora-root-url: ../
---

## salt

spark 에서 salt 라고 하면 랜덤하게 생성한 hash 를 의미한다. (key, value) 형태의 데이터에 대한 aggregation 을 수행할 때, 동일한 key 의 데이터가 하나의 파티션에 몰리게 되는데 이 크기가 너무 커지면 작업을 진행할 수 없다.

이렇게 한쪽에 몰리는 데이터를 skewed 되었다고 하는데, 이런 경우 나머지 대부분의 파티션은 매우 작은고 일부 파티션이 매우 크며 그로 인해 작업이 실패하게 된다.

salt 는 key 에 랜덤한 문자열을 붙여서 partition 을 나누어준다. partition 을 추가로 나누었기 때문에 연산을 한 번 더 해야 한다.

따라서 두 번에 나누어 연산하더라도 문제가 없는 것들만 할 수 있다.

## salted join

join 하려는 두 데이터를 각각 left, right 라고 하면, 우선 데이터가 큰 쪽을 left 로 두고 key 에 salt 를 더해준다. 그리고 right 에도 salt를 더해주는데 이때 주의할 점은, right 는 salt 의 가짓수 만큼 복제되어야 한다는 것이다. left 입장에서 key + salt 에 대항하는 키가 right 상에 반드시 존재해야 하기 때문이다. 따라서 right를 복제할 수 있는 수준에서 salt 의 가짓수가 정해져야 한다. 만약 left 도 매우 크고 right 도 매우 커서 복제할 수 없는 경우는 이 방법을 사용할 수 없게 된다.










```
def enableSalt(s: String): String = {
  val salt = scala.util.Random.nextInt(100)
  f"$salt%02d${s}" 
}
```

```
def disableSalt(s: String): String = s.substring(2)
```

```
val enableSaltUdf = udf(enableSalt _)
val disableSaltUdf = udf(disableSalt _)
```

```
val d2 = d1.select(enableSaltUdf($"dst").as("dst"), $"within", $"between").groupBy("dst").agg(
  count("*").alias("indeg").as[Int],
  sum("within").alias("within").as[Int],
  sum("between").alias("between").as[Int]
)
```

```
val d3 = d2.select(disableSaltUdf($"dst").as("dst"), $"indeg", $"within", $"between").groupBy("dst").agg(
  sum("indeg").alias("indeg").as[Int],
  sum("within").alias("indeg-within").as[Int],
  sum("between").alias("indeg-between").as[Int]
)
```


