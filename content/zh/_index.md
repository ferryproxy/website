---
title: "Home"
---

# Ferry Proxy

Ferry 是一个 Kubernetes 多集群通信组件，它消除了集群之间的通信差异，就好像它们在一个集群中一样，无论这些集群所处的网络环境如何。

Ferry 的主要思想是将一个集群的 Service 映射到另一个集群，另一个集群的应用程序只需要正常访问 Service 即可。

Ferry 项目中的 Tunnel 组件主要用于打通不同集群之间的通信，对集群当前使用的网络环境和网段没有要求。

## 公有云 对 公有云

<img src="/images/cloud-to-cloud.png" width="600">

## 公有云 对 私有云

<img src="/images/cloud-to-edge.png" width="600">

## 私有云 对 公有云

<img src="/images/edge-to-cloud.png" width="600">

## 私有云 对 私有云

<img src="/images/edge-to-edge.png" width="800">


## 示例

Ferry 定义了一个非常简单 API 用于配置 Service 在集群之间的映射规则

可以非常简单的描述哪些 Service 需要暴露给其他集群

<img src="/images/case.png" width="800">

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
metadata:
  name: ferry-rule
  namespace: ferry-system
spec:
  exports:
    - hubName: cluster-1
      service:
        namespace: default
        name: app-1
  imports:
    - hubName: cluster-0
      service:
        namespace: default
        name: app-1
```

## 如何使用 Ferry

 查阅[快速开始](./docs/user/quick-start)
