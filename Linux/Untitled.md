centos 6.5下安装、配置并启动SSH远程访问

1.登录centos 6.5系统，使用root用户登录，如果为非root用户则执行su或su - 或su root或su - root切换为root用户。


2.查看SSH是否安装（检查是否装了SSH包）。
输入命令：rpm -qa | grep ssh
如图所示说明centos 6.5系统已经为我们默认安装了SSH包。

注：若没安装SSH则可输入：yum install openssh-server安装。
3.查看SSH服务是否正在运行。
输入命令：/etc/init.d/sshd status
如图所示centos 6.5系统中SSH服务已经处于运行状态。

4.若centos 6.5系统中SSH服务处于非运行状态则使用（service sshd start）命令开启SSH服务；停止SSH服务命令（service sshd stop）；重启SSH服务命令（service sshd restart）。为了演示效果，我这里先停止SSH服务，然后启动SSH服务，再接着重启SSH服务。
[service sshd stop] -> [/etc/init.d/sshd status] -> [service sshd start]-> [service sshd restart] ->[重启后可输入：netstat -antp | grep sshd 查看是否启动22端口]

5.检查SSHD是否在本运行级别下设置为开机启动
输入命令：chkconfig --list sshd
如图所示centos 6.5系统中SSH服在本运行级别下已经设置为开机启动,如果没设置启动就使用如下命令[chkconfig --level 2345 sshd on]设置下即可。

6.设置SSH服务为开机启动。
输入命令：chkconfig sshd on 即可。
注：若是chkconfig sshd off则禁止SSH开机启动。

​           

怎么查修改ssh服务的默认端口22重启ssh

1、查看当前服务端口
     一般ssh服务的默认端口为22端口，查看监听的端口用netstat，如下：

netstat -tnlp |grep ssh

2.1 修改配置文件
     利用修改配置文件的方法来修改ssh服务的默认端口

vim /etc/ssh/sshd_config

2.2 重启ssh服务

