---
title: 管理多个ssh主机
tags:
	- ssh

categories:
	- linux
---

新公司使用mac办公，以前都是用windows，使用xshell管理服务器，发现并没有mac版本的。
听说其他方式据说不是很稳定，那么就决定自己使用ssh_config文件管理。

#### 基础工作

1. 生成本地ssh密钥，这里对密钥生成不做介绍。
2. 将公钥文件所有内容拷贝到你需要 **远程的用户** 的~/.ssh/authorized_keys文件中，如果文件不存在，就创建。
3. 配备ssh config文件

#### 设置config文件

1. 进入～/.ssh/文件夹：cd ~/.ssh/
2. 创建或修改config文件： vim config
3. 加入要远程主机的内容:

```yaml
Host remote_server
  Hostname x.x.x.x
  Port 22
  User root
  Identityfile ~/.ssh/id_rsa

 Host remote_server2
  Hostname x.x.x.x
  Port 22
  User root
  Identityfile ~/.ssh/id_rsa
```

4. 远程：ssh remote_server/ ssh remote_server2。

