### IDEA 改完主程序的包后，启动报错
报错内容： 找不到或无法加载主类
解决方案：把工程下面的.idea目录下的workspace.xml里面的SPING_BOOT_MAIN_CLASS的路径改成你最新的路径即可 
### 无法下载源码：
pom.xml同级目录执行 mvn dependency:resolve -Dclassifier=sources

