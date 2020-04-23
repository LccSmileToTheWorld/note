时间戳：当前时间与1970年1月1日0分0秒之间以毫秒为单位的时间差。

#java.lang.System

System.currentTimeMillis()：获取时间戳

# java.util.Date

new Date()：无参构造器

new Date(long time)：以时间戳作为参数的构造器

getTime()：返回时间戳

toString()：返回以下形式的字符串： dow mon dd hh:mm:ss zzz yyyy。其中：dow 是一周中的某一天 (Sun，Mon，Tue，Wed，Thu，Fri，Sat) ；zzz 是时间标准。



java.util.Date 怎么转换为 java.sql.Date，java.sql.Date是java.util.Date的子类
1. java.util.Date获取时间戳
2. java.sql.Date有参构造器

#  java.text.SimpleDateFormat

Date 类的 API 不易于国际化，大部分被废弃了， java.text.SimpleDateFormat类是一个不与语言环境有关的方式来格式化和解析日期的具体类。

格式化：日期-->文本 

解析：文本-->日期



SimpleDateFormat () ：无参构造器。以默认的模式和语言环境创建对象

SimpleDateFormat (String pattern)：有参构造器，可以用参数 pattern指定的格式创建一个对象

format(Date date)：格式化

parse(String source)：解析

![](C:\Users\lcc\Desktop\study\Typora\note\JavaSE\11、时间类\1231.png)



