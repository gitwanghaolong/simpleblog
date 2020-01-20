---
title: 解决MAC 安装绿联网卡驱动无效问题
date: 2018-04-19 10:32:41
tags:
- mac
- 网卡
- 绿联
category:
- 我会修电脑
- mac
---
{% asset_img mac.png This is mac logo %}
因为mac的新特性
>System Integrity Protection（系统完整性保护），它是为了保护系统进程，文件，文档不被其它进程修改
>
所以这里需要关闭它，才能读取我们安装的驱动
#### 开启方法
```
1.重启电脑,启动时按住 Command 和 R 键;
2.进入恢复界面后,在右上角工具中打开 终端;
3.输入: csrutil enable  --without kext 
4.重启电脑
5.重启后如果网卡没有生效可以打开终端执行:
sudo kextutil -v 你自己的驱动文件.kext
6.解决每次重启后,重新加载的问题,将上面这句话加入到环境变量中,登陆自动执行
打开:~/.bash_profile
追加:sudo kextutil -v 你自己的驱动文件.kext
保存
```
## ps
驱动文件位置在 /Library/Extensions/安装的驱动名.kext
