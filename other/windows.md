host 文件路径：C:\Windows\System32\drivers\etc
# win+R 运行
桌面图标设置：rundll32.exe shell32.dll,Control_RunDLL desk.cpl,,0
命令行：cmd
远程桌面：mstsc
控制面板：control
注册表：regedit
服务：services.msc
网络连接：ncpa.cpl
计算机详情：dxdiag
计算机用户：netplwiz

# cmd 命令行

本机网络配置：ipconfg

本机和其他主机能否通信：ping [目标ip]

本机和其他主机程序能否通信：telnet [目标ip] [目标port]

清空命令行：cls

查看本机是几核几线程：

* vmic——cpu get *：NumberOfCores为核数，NumberOfLogicalProcessors为线程数

* 任务管理器——性能——CPU：内核为核数，逻辑处理器为线程数

查看环境变量：echo %[变量名]%