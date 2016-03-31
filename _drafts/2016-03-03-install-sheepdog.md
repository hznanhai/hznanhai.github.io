---
layout: post
title: "install sheepdog"
description: ""
category:
tags: []
---

# centos6.5安装配置sheepdog
## 安装
1. 安装必要的软件
```
yum install -y make automake autoconf gcc nss-devel wget git glib2 glib2-devel libtool libqb libqb-devel fuse-devel
```
2. 安装yasm
```
wget http://www.tortall.net/projects/yasm/releases/yasm-1.3.0.tar.gz
tar zxvf yasm-1.3.0.tar.gz
cd yasm-1.3.0
./configure
make && make install
```
3. 安装liburcu
```
git clone https://github.com/urcu/userspace-rcu.git
cd userspace-rcu
./bootstrap
./configure
make && make install
ldconfig
```
4. 升级corosync到最新版
```
yum remove corosync corosynclib corosynclib-devel -y
git clone git://github.com/corosync/corosync.git
cd corosync
git checkout -b needle origin/needle
./autogen.sh
./configure
make && make install
```
5. 安装sheepdog
```
git clone git://github.com/sheepdog/sheepdog.git
cd sheepdog
./autogen.sh
./configure
make install
```

6. 安装新版qemu
```
wget http://wiki.qemu-project.org/download/qemu-2.5.0.tar.bz2
tar xvf qemu-2.5.0.tar.bz2
cd qemu-2.5.0
./configure
make && make install
```
## 配置
