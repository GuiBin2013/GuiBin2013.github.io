---
title: 三月日记
tags:
	- 日记
categories:
	- 日记
---


#### 3月18日

  今天是正式加入cvte的一天，感觉一切都挺好的，良好的办公环境，饭堂，同事，薪资虽然不算高，但自己也能接受。
  第一个要做的是服务器端的监控程序，虽然这和后端开发的工作也能有所出入。
  但自己也能接受，毕竟又能增加自己的知识了，例如docker，集群，分布式，数据库。
  一开始确实没什么思路，google一下，了解了一下当前的监控软件，zabbix, nagios等，感觉都不符合我们的需求。请教了隔壁同事，于是投入了prometheus+grafana的坑里。
  晚上重新购买了云服务器(阿里云好贵，华为云真的是xx)，简单的搭了个docker的服务

#### 3月19日
```python

"""
正式开始工作啦！
首先是学习了一下docker:
学习到：
 1. docker ps (-a)
 2. docker rm container
 3. docker logs -f -t --tail 10 contailer # 日志
 4. docker run 
 5. docker stop/restart/start container
待学习： 
 1. docker和虚拟机的区别(还需要加强理解！！)
 2. docker挂载问题，尤其是mac问题
 3. docker相关的文件位置知识
接着是prometheus：
学习到：
 1. prometheus的基本框架
 2. 简单的exporter的功能，例如node_exporter, cadvisor
待学习：
 1. 时序型数据库知识
 2. 整个prometheus的基本框架工作流程
最后是grafana:
学习到：
 1. grafana的基本使用
 2. dash的使用
待学习： 完整了解整个过程

总的来说：
 今天主要完成了一个docker+prometheus+grafana的简单demo运行，学习docker相关知识。
 但还有一系列的问题需要考虑，如gpu如何监控，docker监控exporter(cadvisor）有些宿主机数据无法读取问题，
 还有一些挂载的问题，性能问题考虑，数据库数据量问题，感觉是个漫长过程，但需要一步步的努力！
"""

```

#### 3月20日

```python
"""
今天的主要工作是完善prometheus+grafana的demo，大致了解grafana的使用方式，dashboard的配置和方法。
尝试了很多开源的模版，发现由于一些作者可能不再进行维护，直接使用需要修改很多操作。以及修复了docker时间不同步的问题。
知识巩固：
 1. docker exec -it container command # 在docker中执行某个命令
 2. docker exec -it container /bin/sh # 进入docker bash界面
 3. docker exec -u root ... # 可以以root用户进入docker docker用户默认是nobody
 4. docker时间同步：
  a. 启动挂载： docker run -v /etc/localtime container:/etc/localtime
  b. 拷贝： sudo docker cp /etc/localtime container:/etc/localtime # 可能localhost链接的文件也需要进行拷贝。
 5. grafana的问题暂时不说了，一知半解真的不行。。

问题问题：
 1. mac的docker挂载问题是个谜啊！！！
 2. 昨天的内容还没来的及了解
"""
```

#### 3月21日

```python
"""
今天的主要工作还是完善prometheus+grafana的demo，写了cadvisor的启动文档查阅了一下gpu监控的方式。
算是基本掌握了grafana的配置方法，了解node_export和cadvisor返回的数值以及一些计算方式。
总的来说，进度还是有点慢！！

知识巩固：
 1. linux系统负载概念，指的是过去x秒平均每年在排队等待cpu执行的进程，不包括那些进入io等待或者主动发起等待的程序，当系统负载/cpu数量<3 才认为系统负载合理。
 2. top看到的是逻辑上的cpu数量，也就是物理cpu数量xcores, 实际上如果支持超线程，逻辑cpu应该还需要x2, 或者说支持cpu x core x 2的线程数
问题问题：
 1. 整个系统需要了解
"""
```




#### 3月22日

```python
"""
啊啊啊，偷懒了2天，今天才补上周五的日志啊。

今天的主要工作还是完善prometheus+grafana的demo，尝试了一些方法把gpu监控集成进去，
nvidia_gpu_export还算顺利部署，也在brafana成功显示出来了
发现cadvisor部署时感觉系统卡顿，初步推测时磁盘io，感觉网络IO的可能性特别小。集成gpu进去也失败了。
还写了一些文档。

知识巩固
	1. 远程相关，把相关信息记载在ssh_config，然后以后就方便ssh.
"""
```


#### 3月25日

```python
"""
今天的主要工作是把prometheus和grafana服务放到了服务器上，并且通过加入一些挂载使得cadvisor不会卡顿，目前看来效果还可以。
另外一个就是把docker GPU集成到cadvisor，花了一下午+晚上的时间，尝试了很多方法，最后终于成功了。
主要问题在于自己阅读官方文档时，一知半解就过了，发现原来没读懂，把nvml的库文件位置挂载错误。
另外cadvisor最新的v0.32.0启动时竟然没有打印日志。。血坑。

知识巩固
	1. linux命令iostat可以查看磁盘io，iostat 2, 3 # 表示2刷新一次，执行3次。
"""
```


