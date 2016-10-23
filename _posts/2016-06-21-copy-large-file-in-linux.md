---
layout: post
title: "copy large file in linux"
description: ""
category:
catalog: true
tags:
    - Linux
    - shell
---

# Linux系统快速拷贝大文件
Linux系统中拷贝几十G的大文件，如果直接用cp、mv或者scp，效率非常底下。经实践可以用nc+pgiz压缩来加快传输。

1. 下载安装pgiz
~~~bash
wget http://pkgs.repoforge.org/pigz/pigz-2.1.6-1.el6.rf.x86_64.rpm
rpm -ivh pigz-2.1.6-1.el6.rf.x86_64.rpm
~~~

2. 在目标机器上起nc服务
~~~bash
nc -l 1234 | pigz -d | tar -C /home/ -xvf -
~~~

3. 从本机传输文件到目标机器的nc端口
~~~bash
tar cv {dir} | pigz | nc {hostname} 1234
~~~
