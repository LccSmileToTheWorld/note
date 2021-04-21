时间戳：指格林威治时间 1970 年 01 月 01 日 00 时 00 分 00 秒（北京时间 1970 年 01 月 01 日 08 时 00 分 00秒）起至现在的总秒数。

#java.lang.System

System.currentTimeMillis()：获取时间戳

# java.util.Date

获取实例

* new Date()：无参构造器

* new Date(long time)：以时间戳作为参数的构造器



常用方法

* getTime()：返回时间戳

* toString()：返回以下形式的字符串： dow mon dd hh:mm:ss zzz yyyy。其中：dow 是一周中的某一天 (Sun，Mon，Tue，Wed，Thu，Fri，Sat) ；zzz 是时间标准。



java.util.Date 怎么转换为 java.sql.Date，java.sql.Date是java.util.Date的子类
1. java.util.Date获取时间戳
2. java.sql.Date有参构造器

#  java.text.SimpleDateFormat

Date 类的 API 不易于国际化，大部分被废弃了， java.text.SimpleDateFormat类是一个不与语言环境有关的方式来格式化和解析日期的具体类。

格式化：日期-->文本 

解析：文本-->日期



获取实例

* SimpleDateFormat () ：无参构造器。以默认的模式和语言环境创建对象

* SimpleDateFormat (String pattern)：有参构造器，可以用参数 pattern指定的格式创建一个对象



常用方法

* format(Date date)：格式化

* parse(String source)：解析

![](C:\Users\lcc\Desktop\study\Typora\note\JavaSE\11、时间类\1231.png)

# java.util.Calendar

Calendar是一个抽象基类，获取实例有两种方式

* 调用Calendar.getInstance()：内部也是创建GregorianCalendar对象

* 创建子类GregorianCalendar对象



常用方法

* toString（）
* getTime()：Calendar--->Date
* setTime(Date date)：Date--->Calendar
* get(int field)：获取想要的时间信息，field：Calendar静态属性
* set(int field, int value)：以field方向改变时间信息
* add(int field, int amount)：以field方向加时间，如果要减时间，将amount参数写成负数



注意

* 获取月份时： 一月是0 ，二月是1，......12月是11
* 获取星期时： 周日是1 ，周二是2，......周六是7



JDK8之前，时间处理不是很理想，如果项目中使用8之前的JDK，可以引用 Joda-Time依赖。JDK8的新时间API，就是在 Joda-Time的基础上开发的。