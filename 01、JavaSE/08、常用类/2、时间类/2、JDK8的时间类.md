JDK8新加的时间类

* java.time：包含值对象的基础包
* java.time.chrono：提供对不同的日历系统的访问
* java.time.format：格式化和解析时间和日期
* java.time.temporal：包括底层框架和扩展特性
* java.time.zone：包含时区支持的类

# java.time.LocalDateTime

类似的类：LocalDate，LocalTime



获取实例

* static now()：以默认时区获取当前时间对象
* static now(ZoneId zone)：指定时区，获取当前时间对象
* static of()：指定时间，创建时间对象



获取时间属性

方法都特别的简单，格式为：getXxx()，只有获取天和月的时候特别

* int year()：获取年份

* int getDayOfYear()：获取指定日期是一年中的第几天
* int getDayOfMonth()：获取指定日期是月份中的几号
* DayOfWeek getDayOfWeek()：获取指定日期是星期几, 返回的是DayOfWeek枚举，可以通过DayOfWeek的getValue()获取1-7



修改时间

格式为：withXxx()，修改天时，分为修改月份中的天（1-31）和修改年份中的天（1-366）

修改时间都需要一个新的时间对象来接收，体现了时间类型的不可变性，这和1.8之前有很大不同。

* LocalDateTime withYear(int year)：修改年
* LocalDateTime withDayOfMonth(int dayOfMonth)：修改月份中的天
* LocalDateTime withDayOfYear(int dayOfYear)：修改年份中的天



加时间

格式都为：plusXxx()

* LocalDateTime plusDays(long days)：加几天



减时间

格式都为：minusXxx()

* LocalDateTime minusDays(long days)：减去几天

# Instant

```java
//返回默认 UTC(格林威治) 时区的 Instant 类的对象
Instant now = Instant.now();

//返回在 1970 01 01 00 00 00 基础上加上指定毫秒数之后的 Instant 类的对象
Instant instant = Instant.ofEpochMilli(123434L);

//instant --> 时间戳
long l = now.toEpochMilli();

//时间戳 --> instant
Instant instant1 = Instant.ofEpochMilli(1589249949518L);

//结合即时的偏移来创建一个OffsetDateTime（带偏移量的时间类）
OffsetDateTime offsetDateTime = now.atOffset(ZoneOffset.ofHours(8));
```
# DateTimeFormatter

该类提供了三种格式化方法：

* 预定义的标准格式。如：ISO_LOCAL_DATE_TIME；ISO_LOCAL_DATE；ISO_LOCAL_TIME
* 本地化相关的格式。如： ofLocalizedDateTime(FormatStyle.LONG)
* 自定义的格式。如： ofPattern(“yyyy MM dd HH:mm:ss”)

格式化：String format(TemporalAccessor temporal)

解析：TemporalAccessor parse(CharSequence text)

