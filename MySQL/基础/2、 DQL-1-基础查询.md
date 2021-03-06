 [toc]
# SQL语法

* 不区分大小写，但建议关键字大写，表名、列名小写
* 每条命令最好用分号结尾
* 每条命令根据需要，可以进行缩进，换行
* 注释
    * 单行注释：# 注释文字
	* 单行注释：-- 注释文字
	* 多行注释：/* 注释文字*/
# 基本查询

## 基本语法

```sql
SELECT  
    <要查询的字段|表达式|常量值|函数>  
FROM
    <表名>
```
## 注意事项
* 给表起别名后，在查询列表中就不能以原始表名作限定了，因为SQL执行顺序是先执行from语句，再执行select语句
* 要根据某个字段**去重查询**时，在字段前加入关键词 **DISTINCT**，当DISTINCT后跟有多个字段时，是以多个字段的拼接结果去重的
* 如果要查询表中所有字段，可以用 *
* +的使用：+ 在SQL中仅仅被用作算术运算，如要拼接字符串，可以使用 CONCAT 函数
    * 数值型 + 数值型 = 和
    * 数值型 + 字符型 = 试图将字符型转换成数字，不可转换的记作0，然后相加
    * 字符型 + 字符型 = 试图将字符型转换成数字，不可转换的记作0，然后相加
    * 任何型 + NULL  = NULL ( CONCAT 函数也是如此，避免NULL，可以使用 IFNULL 函数)
* 常量值：数字，字符串
* 表达式：加减乘除，取模
* 查询的字段可以起别名
    * 字段 别名  
    * 字段  AS 别名
    * 当别名为多个单词组成时，需要用双引号或单引号引起来
# 条件查询--WHERE
## 基本语法
```sql
SELECT  
    <要查询的字段|表达式|常量值|函数>
FROM
    <表名>
WHERE   <条件1>   AND   <条件2>
```
## 查询列表分类
* 条件表达式：
	* <
	* <
	* =
	* <=
	* =
	* <> 或 != 
	* **IS NULL**
	* **IS NOT NULL** 
	* <=> ：安全等于，既可以判断字段是否为NULL，也可以判断是否等于某字符 
* 逻辑表达式：
  * AND 或 &&
  * OR 或 ||
  * NOT
* 模糊查询：
  * LIKE：通常配合通配符进行模糊查询
    * % ：匹配多个字符，包含0个
    WHERE name LIKE '%张%'：查询name为张，或为 xx张xx 的数据
    * _ ：匹配一个字符 
    WHERE name LIKE '_张%'：查询name第二个字为张的数据
    当 % 和 _ 当作模糊查询条件时
    * 使用\进行转义
       WHERE name LIKE '_ \ _%'：查询name第二个字为 _ 的数据
    * 使用**ESCAPE**关键字声明转义字符
       WHERE name LIKE '_&_%' ESCAPE &：查询name第1个字为& 的数据
  * BETWEEN <小临界值] AND [大临界值>
    * 结果包含临界值 
    * 俩个临界值不能颠倒顺序
  * IN：判断字段是否等于IN列表中的某一项
## 注意事项
问题：
SELECT * FROM USER WHERE NAME LIKE '%%';
SELECT * FROM UER;
上述两个sql执行结果是否一样
结果：
当name属性有为NULL时，不一样
当name属性都不为NULL时，一样
# 排序查询--ORDER BY
## 基本语法
```sql
SELECT  
    <要查询的字段|表达式|常量值|函数>
FROM
    <表名>
ORDER BY
    <排序的字段|表达式|函数> ASC|DESC
```
## 注意事项
* **ASC**：正序，ORDER BY 默认为正序
* **DESC**：倒叙
* ORDER BY 支持多个字段排序，以逗号分隔，排序优先级从前往后
* ORDER BY 语句放在SQL最后，除了LIMIT
***
# 分组查询--GROUP BY
## 基本语法
```sql
SELECT  
    <group by后的字段|聚合函数>  
FROM
    <表名>
GROUP BY
    <分组字段|函数|表达式>
```
## 注意事项
**分组查询的查询列表比较特殊，要求是分组函数或group by后出现的字段**
可以按多个字段分组，分组字段不分先后顺序（只有所有分组字段都一致，才会被分为一组）
## 筛选条件分类
* 分组前筛选
```sql
SELECT  
    <group by后的字段|聚合函数>
FROM
    <表名>
WHERE 
    <筛选条件>
GROUP BY
    <分组字段|函数|表达式>
```
* 分组后筛选
```sql
SELECT  
    <group by后的字段|聚合函数>
FROM
    <表名>
GROUP BY
    <分组字段|函数|表达式>
HAVING 
    <筛选条件>
```
筛选条件在原始表中，就用where筛选；
筛选条件在分组后的临时表中，就用having筛选；
当两者都满足时（筛选条件就是group by后的分组字段），推荐使用where筛选（效率高）。
# 分页查询--limit
## 基本语法

```sql
SELECT  
    <要查询的字段|表达式|常量值|函数>
FROM
    <表名>
LIMIT <index>, <size>
```
```sql
SELECT
	<要查询的字段|表达式|常量值|函数> 
FROM
	<表名>
LIMIT <size> OFFSET <index>
```



## 注意事项

* index：索引，起始索引从0开始，可以不写，默认从0开始
* size：查询的最大条数
* 第一中语法：写index时，index和size中间有一个逗号