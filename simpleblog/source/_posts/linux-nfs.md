---
title: linux远程目录挂载
date: 2019-08-18 18:02:28
tags:
- linux
category:
- 代码和我
- linux
---
{% asset_img linux.jpg This is lunix nfs %}
### 什么是NFS ?
&nbsp; &nbsp; NFS就是Network File System的缩写，它最大的功能就是可以通过网络，让不同的机器、不同的操作系统可以共享彼此的文件。
&nbsp; &nbsp; NFS服务器可以让PC将网络中的NFS服务器共享的目录挂载到本地端的文件系统中，而在本地端的系统中来看，那个远程主机的目录就好像是自己的一个磁盘分区一样，在使用上相当便利；
&nbsp; &nbsp; NFS一般用来存储共享视频，图片等静态数据。
### 提供目录的主机
```
1.基础服务
yum install nfs-utils
2.修改 /etc/exports,增加共享目录(多ip限制)
/opt/tmp/ 192.168.0.1(rw,sync,no_root_squash)
/opt/tmp/ 192.168.0.2(rw,sync,no_root_squash)
/opt/tmp/ 192.168.0.3(rw,sync,no_root_squash)
3.启动
先执行
systemctl restart rpcbind 
再执行
systemctl restart nfs
4.查看共享
showmount -e
```
### 使用目录的主机
```
1.基础服务
yum install nfs-utils
2.启动
先执行
systemctl restart rpcbind 
再执行
systemctl restart nfs
3.挂载
mount -t nfs 192.168.0.1:/opt/tmp/  /opt/tmp/
4.查看挂载
df -h
5.解除挂载
umount /opt/tmp /opt/tmp
```