---
title: "技术原理"
---

# 技术原理

## 通信和穿透

Ferry-Tunnel 之间使用 ssh 协议的能力实现通信和穿透

主要使用以下能力
- [direct-tcpip][tcpip]
- [tcpip-forward][tcpip]
- [direct-streamlocal][streamlocal]
- [streamlocal-forward][streamlocal]

[streamlocal]: https://github.com/openssh/openssh-portable/blob/master/PROTOCOL
[tcpip]: https://datatracker.ietf.org/doc/html/rfc4254

核心就两点
- 监听本地一个端口, 连接上对端的 Ferry-Tunnel, 并通过其转发所有连接
- 连接上对端的 Ferry-Tunnel 并监听一个端口, 转发监听端口的连接到本地

## 服务发现

每一个导出的服务端口都会在导入的集群中的 Ferry-Tunnel 分配一个端口

Ferry 会在导入的集群创建 Headless Service 指向本集群的 Ferry-Tunnel 对应服务的端口
