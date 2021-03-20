 [toc]
# 常见函数分类
* 单行函数
    * 字符函数
    * 数学函数
    * 日期函数
    * NULL函数
    * 流程控制函数
    * 系统函数
* 聚合函数/分组函数/统计函数
# 字符函数
* **concat(str1, str2, ...)**：拼接字符
* **substr 或 substring**：截取字符，初始索引为1
    * substr(str, num)：从第num个字符截取str，
    substr("abcd", 2)--> 'bcd' 
    * substr(str, num1, num2)：从第num1个字符截取str，截取num2个字符
    substr("abcd", 2, 2)--> 'bc'
* **instr(str1, str2)**：查询子串在父串中第一次出现的索引，找不到则返回0
instr('abcd123', 'd1')--> 4
* **upper(str)**：将字符转换成大写
* **lower(str)**：将字符转换成小写
* **length(str)**：获取字符的字节长度
单个汉字长度根据数据库字符集不同而变化（UTF-8：3、GBK：2）
* **trim**：
    * trim(str)：去除首尾空格
    trim(' sfs  sdf ')--> 'sfs sdf'
    * trim('str1' from 'str2')：去除str2中的首尾str1
    trim('aa' FROM 'aaaaa哈哈aaa嗯哼a')--> 'a哈哈aaa嗯哼a'
* **lpad(str1, num, str2)**：用str2左填充str1，使其达到字符长度为num的字符
lpad('啊哈', 3, 'aa')--> 'a啊哈'
lpad('啊哈', 1, 'aa')--> '啊'
* **rpad(str1, num, str2)**：用str2右填充str1，使其达到字符长度为num的字符
rpad('啊哈', 3, 'aa')--> '啊哈a'
rpad('啊哈', 1, 'aa')--> '啊'
* **replace(str1, str2, str3)**：将str1中的所有str2替换成str3
 REPLACE('aaabcda', 'aa', 'e')--> 'eabcda'
REPLACE('abcda', 'f', 'e')--> 'abcda'
***
# 数学函数
* **round**
     * round(num)：四舍五入，保留整数
            round(1.645)--> 2
            round(-1.645)--> -2
    * round(num1, num2)：对num1进行四舍五入，结果保留num2位小数
             round(1.645, 2)--> 1.65
             round(-1.645, 2)--> -1.65
* **ceil(num)**：对num进行向上取整
ceil(1.01)--> 2
ceil(1.00)--> 1
ceil(-1.01)--> -1
* **floor(num)**：向下取整
floor(1.01)--> 1
floor(1.00)--> 1
floor(-1.01)--> -2
* **truncate(num1, num2)**：对num1进行截取，保留小数点num2位
truncate(1, 1)-->1
truncate(1.99, 1)--> 1.9
truncate(-1.99, 1)--> -1.9
* **mod(num1, num2）**：取模，num1%num2
 结果的正负和被除数保持一致
mod(10, 3)--> 1
mod(-10, -3)--> -1
***
# 日期函数
* 当前时间 
    * **now()**：当前日期+时间
    * **curdate()**：当前日期
    * **curtime()**：当前时间
* 指定日期
    * **year(date)**：获取指点日期的年
    * **month(date)**：获取指定日期的月
    * **monthname(date)**：获取指定日期的月的英文名
    * **weekofyear(date)**：获取指定日期在当年是第几周
    * **day(date)**：获取指定日期的日
    * **datediff(date1, date2)**：查询两个时间相差几天，如果date2大于date1，则返回负数
    * **dayname(date)**：获取指定日期是星期几的英文名称
    * **dayofweek(date)**：获取指定日期是这周的第几天，周日算作第一天
    * **dayofmonth(date)**：获取指定日期是当月的第几天
    * **dayofyear(date)**：获取指定日期是当年的第几天
    * **hour(date)**: 获取指定日期的小时
    * **minute(date)**: 获取指定日期的分
    * **second(date)**: 获取指定日期的秒
*  其他
    * **str_to_date(str, formate)**：将str转换成日期格式，并根据formate格式化  
    STR_TO_DATE('2019-08-22 00:01:02', '%Y-%m-%d') --> 2019-08-22
    * **date_format(date, formate)**：将date转换成字符串，并根据formate格式化
     DATE_FORMAT('2019-08-22 00:01:02', '%Y年%c月%d日') --> 2019年8月22日
            
| 格式符 | 功能               |
| ------ | ------------------ |
| %Y     | 四位的年份         |
| %y     | 两位的年份         |
| %m     | 月份（01,02...12） |
| %c     | 月份（1,2...12）   |
| %d     | 日（01,02...）     |
| %H     | 小时（24小时制）   |
| %h     | 小时（12小时制）   |
| %i     | 分钟               |
| %s     | 秒                 |
# NULL函数
* **ifnull(expr1, expr2)**：expr1不为NULL，返回expr1，否则返回expr2
IFNULL(1/0, '嗯哼') --> 嗯哼
* **isnull(expr)**：判断expr是否为null，是null返回1，不是返回0
* **nullif(expr1, expr2)**：判断expr1==expr2，相等返回NULL，不相等返回expr1
# 流程控制函数
* **if(expr1, expr2, expr3)**：处理单分支，如果表达式为true，则返回expr2，否则返回expr3
IF(10<5,'正确', '错误') --> 错误
IF(10>5,'正确', '错误') --> 正确
IF(NULL,'正确', '错误') --> 错误
* **case**：处理多分支
    * 处理等值判断：类似switch case
    
	  ```sql
	  CASE <字段/表达式>
	  WHEN <常量1> THEN <值1>
	  WHEN <常量2> THEN <值2>
     ...
     ELSE <值n>
     END
	  ```
	
	* 处理条件判断：类似多重if
	
     ```sql
     CASE
     WHEN <条件1> THEN 值1
     WHEN <条件2> THEN 值2
     ...
     ELSE <值n>
     END
     ```
# 系统函数
   * **version()**：查询mysql版本
   * **user()**：查询当前连接用户
   * **database()**：当前连接数据库
# 聚合函数
* **sum(字段)**：求和
* **avg(字段)**：求平均数
* **max(字段)**：求最大值
* **min(字段)**：求最小值
* **count**
    * count(字段)：某字段不为NULL的数据个数
    * count(1)：所有数据的个数
    * count(*)：所有数据的个数

注意事项：
* sum, avg用作数值处理
* max，min，count可以处理任何类型数据
* 聚合函数都忽略NULL值。但是count(1)相当于又加了一列1，查询列1的个数，所以查询结果是所有数据的个数。count(*)是以所有字段查询，一条数据不可能所有字段都为null，所以查询结果也是所有数据的个数。
* 和聚合函数一起查询的字段要求是 group by 后的字段，否则没有意义
* 聚合函数可以搭配关键字 DISTINCT 使用，先去重再计算
count(distinct name)：名字不一样的有多少条
* MYISAM引擎下，count(\*)的效率高
INNODB引擎下，count(\*)和count(1)的效率差不多，都比count(字段)的效率高 