본 글에서는 scala 에서 어떻게 날짜와 시간을 처리하는지 알아본다.

## Date and Calendar

아래 3개 패키지를 사용한다.

```
import java.text.SimpleDateFormat
import java.util.Calendar
import java.util.Date
```

`java.util.Date` 이용해 오늘 날짜 구하기

```scala
val now = new Date()
java.util.Date = Thu Jul 19 10:50:51 KST 2018
```

`java.util.Date`가 범용적인 날짜 객체다. 다만 날짜 연산을 지원하지 않기 때문에 별도로 Calendar 객체를 사용하는 경우가 있다.

`java.util.Calendar` 이용해 오늘 날짜 구하기

```scala
val cal = Calendar.getInstance()
cal.getTime()
```

연산을 지원한다.

```scala
val cal = Calendar.getInstance()
cal.add(Calendar.MONTH, -1)
cal.getTime()
```

두 날짜를 비교한다. 연산할 때는 Calendar 에서 했지만 단순 비교는 `java.util.Date` 상에서 가능하다.

```scala
val c1 = Calendar.getInstance()
val c2 = Calendar.getInstance()

c1.add(Calendar.MONTH, -1)  // 1 month ago
c2.add(Calendar.MONTH, -2)  // 2 month ago

val d1 = c1.getTime
val d2 = c2.getTime

d1.after(d2)  // d1 is after than d2
```

## Elapsed 

작업 수행 시간을 측정하고자 할 때는 java.util.Date 가 아니라 그냥 System 을 사용한다.

```scala
val start = System.currentTimeMillis
// do something
val totalTime = System.currentTimeMillis - start
``` 

```scala
val start = System.nanoTime
// do something
val totalTime = System.nanoTime - start
``` 

