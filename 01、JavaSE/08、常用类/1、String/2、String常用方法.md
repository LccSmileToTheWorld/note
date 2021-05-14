[toc]
# String的判断方法 
equals(String anotherString)：判断两个字符串的内容是否一致 
equalsIgnoreCase(String anotherString)：忽略大小写，判断两个字符串的内容是否一致

isEmpty()：判断字符串是否为空 

endsWith(String suffix)：测试此字符串是否以指定的后缀结束 
startsWith(String prefix)：测试此字符串是否以指定的前缀开始 
startsWith(String prefix, int toffset)：测试此字符串从指定索引开始的子字符串是否以指定前缀开始

contains(CharSequence s)：当且仅当此字符串包含指定的 char 值序列时，返回 true

matches(String regex)：判断字符串是否匹配给定的正则表达式
# String 与 byte[]之间的转换
* 编码：String --> byte[]:调用String的getBytes()
    * getBytes()：以默认的编码方式，转换成字节数组 
    * getBytes(String charsetName)：指定编码方式，转换为字节数组
* 解码：byte[] --> String:调用String的构造器 
    * String(byte bytes[])：以默认的编码方式解码 
    * String(byte bytes[], String charsetName)：以指定编码方式解码

编码：字符串 -->字节  (看得懂 --->看不懂的二进制数据)
解码：编码的逆过程，字节 --> 字符串 （看不懂的二进制数据 ---> 看得懂）

说明：解码时，要求解码使用的字符集必须与编码时使用的字符集一致，否则会出现乱码。
# String 与 char[]
length()：获取字符串长度
toCharArray()：转换为字符数组
String(char value[])：调用String构造方法，字符数组转换为字符串
charAt(int index)：返回字符数组下角标为index的字符
# String 与包装类转换
基本类型转换为String，调用String的静态方法：valueOf()
String转换为基本类型，调用包装类的静态方法：parseXx()
# 英文大小写转换
toLowerCase()：转换为小写
totoUpperCase()：转换为大写

# 截取字符串
substring(int start)：从start到结尾截取字符串
substring(int start, int end)：从start到end截取字符串，左闭右开，包头不包尾
# 去掉首尾空格
trim()：去掉首尾空格
# 查找子串
indexOf(String str)：返回子串在父串中第一次出现处的索引，没有返回-1
indexOf(String str, int fromIndex)：从指定的索引开始查找，返回子串在父串中第一次出现处的索引，没有返回-1。（索引是从0开始的，不是从参数fromIndex开始的）

lastIndexOf(String str)：返回指定子串在父串中最右边出现处的索引，没有返回-1
lastIndexOf(String str, int fromIndex)：从指定的索引开始查找，返回指定子串在父串中最右边出现处的索引，没有返回-1
# 替换
replace(char oldChar, char newChar)：返回一个新的字符串，它是通过用 newChar 替换此字符串中出现的所有 oldChar 得到的
String replaceAll(String regex, String  replacement)：使用给定的 replacement 替换此字符串所有匹配给定的正则表达式的子字符串。
String replaceFirst(String regex, String replacement)：使用给定的 replacement 替换此字符串匹配给定的正则表达式的第一个子字符串。
# 分割
split(String regex)：根据给定正则表达式来拆分字符串。
split(String regex, int limit)：根据匹配给定的正则表达式来拆分字符串，最多不超过limit个，如果超过了，剩下的全部都放到最后一个元素中。
# 其他
concat(String str)：拼接字符串，等同于+
compareTo(String anotherString)：比较两个字符串大小，返回两者第一个不同字符（同下角标对比）的ASCII码值差，调用者-参数，可以为负数。如果两个字符串的长度不同，并且前面N（较短字符串的长度）个字符都相等，则返回两个字符串长度之差。

format()：格式化字符串。
eq：数字转 String 固定位数，不足补零。String.format("%04d", 22); //打印   0022
0 代表前面要补的字符 
4 代表字符串长度
d 表示参数为整数类型

