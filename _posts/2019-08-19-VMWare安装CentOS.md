---
layout:     post
title:      VMWare安装CentOS
subtitle:   VMWare虚拟机安装CentOS教程
date:       2019-08-19
author:     LongtaoSu
header-img: img/post-bg-re-vs-ng2.jpg
catalog: true
tags:
    - CentOS
---

> 本文忽略CentOS的配置安装过程，重点讲述如何配置网络，详情查看参考

说明：CentOS 7.0默认安装好之后是没有自动开启网络连接的！

cd  /etc/sysconfig/network-scripts/  #进入网络配置文件目录

![img](https://www.osyunwei.com/wp-content/uploads/2014/07/3003.jpg)

vi  ifcfg-eno16777736  #编辑配置文件，添加修改以下内容

![img](https://www.osyunwei.com/wp-content/uploads/2014/07/3004.jpg)

HWADDR=00:0C:29:8D:24:73

TYPE=Ethernet

BOOTPROTO=static  #启用静态IP地址

DEFROUTE=yes

PEERDNS=yes

PEERROUTES=yes

IPV4_FAILURE_FATAL=no

IPV6INIT=yes

IPV6_AUTOCONF=yes

IPV6_DEFROUTE=yes

IPV6_PEERDNS=yes

IPV6_PEERROUTES=yes

IPV6_FAILURE_FATAL=no

NAME=eno16777736

UUID=ae0965e7-22b9-45aa-8ec9-3f0a20a85d11

ONBOOT=yes  #开启自动启用网络连接

IPADDR0=192.168.21.128  #设置IP地址

PREFIXO0=24  #设置子网掩码

GATEWAY0=192.168.21.2  #设置网关

DNS1=8.8.8.8  #设置主DNS

DNS2=8.8.4.4  #设置备DNS

:wq!  #保存退出

service network restart   #重启网络

ping www.baidu.com  #测试网络是否正常

![img](https://www.osyunwei.com/wp-content/uploads/2014/07/3005.jpg)

ip addr  #查看IP地址

![img](https://www.osyunwei.com/wp-content/uploads/2014/07/3006.jpg)

**三、设置主机名为www**

hostname  www  #设置主机名为www

vi /etc/hostname #编辑配置文件

www   #修改localhost.localdomain为www

:wq!  #保存退出

vi /etc/hosts #编辑配置文件

127.0.0.1   localhost  www   #修改localhost.localdomain为www

:wq!  #保存退出

shutdown -r now  #重启系统

**至此，CentOS 7.0系统安装配置图解教程完成**





参考

https://www.osyunwei.com/archives/7829.html

https://blog.csdn.net/baidu_32523857/article/details/82880678

https://www.cnblogs.com/owaowa/p/6123902.html