
scala 에서 로그 계산하는 방법을 알아본다. 굳이 기록으로 남기는 이유는 log2 가 없기 때문이다.

밑이 자연상수인 것과 10 인 것은 함수가 존재한다.

```
scala.math.log
scala.math.log10
```

밑이 2 인 로그는 직접 만들어써야 한다.

``
def log2(x: Double): Double = scala.math.log(x) / scala.math.log(2)
```
