# 安装
1. 到[官网](https://www.oracle.com/technetwork/java/javase/downloads/index.html)下载对应版本，操作系统位数的JDK安装文件。
2. 傻瓜式安装
# 环境配置
1. 右键计算机-->点击属性
2. 点击高级系统设置-->点击环境变量
![](..\2、环境配置\2970_1.png)
3. 在系统变量那栏，新建环境变量JAVA_HOME
变量名：JAVA_HOME
变量值：JDK安装位置
![](..\2、环境配置\2974_1.png)
4. 修改path变量
添加%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
![](..\2、环境配置\2978_1.png)
5. 新建环境变量CLASSPATH
变量名：CLASSPATH
变量值：.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
![](..\2、环境配置\2976_1.png)
# 验证
1. 打开命令行窗口
2. 输入java -version，回车
![](C:\Users\lcc\Desktop\study\Typora\note\JavaSE\2、环境配置\2980_1.png)