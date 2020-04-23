# 异同
String：不可变的字符序列；JDK1.0就有；底层使用char[]存储 
StringBuffer：可变的字符序列；JDK1.0就有；底层使用char[]存储；线程安全的，效率低； 
StringBuilder：可变的字符序列；jdk5.0新增的；底层使用char[]存储；线程不安全的，效率高； 

对比String、StringBuffer、StringBuilder三者拼接字符串的效率： 从高到低排列：StringBuilder > StringBuffer > String
# 源码分析：
String str = new String() --> char[] value = new char[0]
String str1 = new String("abc") --> char[] value = new char[]{'a','b','c'}
StringBuffer sb1 = new StringBuffer() --> char[] value = new char[16]：底层创建了一个长度是16的数组。 
sb1.length()：返回的是count属性，不是char[]的length
sb1.append('a') --> value[0] = 'a'
sb1.append('b') --> value[1] = 'b'
StringBuffer sb2 = new StringBuffer("abc") --> char[] value = new char["abc".length() + 16]

扩容问题：如果要添加的数据底层数组盛不下了，那就需要扩容底层的数组。 
默认情况下，扩容为原来容量的2倍 + 2，同时将原有数组中的元素复制到新的数组中。
指导意义：开发中建议大家初始化容量：StringBuffer(int capacity) 或 StringBuilder(int capacity) 
# 常用方法

* 增：
    * append(xx)：在尾部添加xxx
    * insert(int offset, xxx)：在角标offset处插入xxx
* 删：
    * deleteCharAt(int index)：删除角标为index的字符
    * delete(int start, int end)：删除脚标为 [start, end) 的字符串，左闭右开，包头不包尾
* 改：
    *  setCharAt(int index, char ch)：将角标为index的字符修改为ch
    *  replace(int start, int end, String str)：将脚标为 [start, end) 的字符串替换为str
* 查： charAt(int index)：查询角标为index的字符
* 长度：length()