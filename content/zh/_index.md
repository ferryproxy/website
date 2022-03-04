---
title: "Home"
---

# Ferry Proxy

Ferry 是一个 Kubernetes 多集群通信组件，它消除了集群之间的通信差异，就好像它们在一个集群中一样，无论这些集群所处的网络环境如何。

Ferry的主要思想是将一个集群的Service映射到另一个集群，另一个集群的应用程序只需要正常访问Service即可。

Ferry项目中的Tunnel组件主要用于打通不同集群之间的通信，对集群当前使用的网络环境和网段没有要求。

![Architecture](/images/architecture.png)

Ferry 定义了一个非常简单 API 用于配置 Service 在集群之间的映射规则

可以非常简单的描述哪些 Service 需要暴露给其他集群

![Case](/images/case.png)

## 如何使用 Ferry

 查阅[快速开始](./docs/user/quick-start)