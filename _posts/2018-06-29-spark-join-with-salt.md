

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


