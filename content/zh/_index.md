---
title: "Home"
---

# Ferry Proxy

Ferry 是一个 Kubernetes 多集群通信组件，它消除了集群之间的通信差异，就好像它们在一个集群中一样，无论这些集群所处的网络环境如何。

Ferry 的主要思想是将一个集群的 Service 映射到另一个集群，另一个集群的应用程序只需要正常访问 Service 即可。

Ferry 项目中的 Tunnel 组件主要用于打通不同集群之间的通信，对集群当前使用的网络环境和网段没有要求。

Ferry 可以简化跨集群中的架构，可用于指标收集、请求跟踪上报、日志上传、连接到无法访问的 Apiserver 等。

## 公有云 对 公有云

<img src="/images/cloud-to-cloud.png" width="600">

[快速开始](./docs/user/examples/default)

## 公有云 对 私有云

<img src="/images/cloud-to-edge.png" width="600">

[快速开始](./docs/user/examples/data-plane-unreachable)

## 私有云 对 公有云

<img src="/images/edge-to-cloud.png" width="600">

[快速开始](./docs/user/examples/control-plane-unreachable)

## 私有云 对 私有云

<img src="/images/edge-to-edge.png" width="800">


## 示例

Ferry 定义了一个非常简单 API 用于配置 Service 在集群之间的映射规则

可以非常简单的描述哪些 Service 需要暴露给其他集群

<img src="/images/case.png" width="600">

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

## 为什么使用 Ferry

- 避免云厂商锁定
    - 让不同云之间可以相互访问
    - 将服务迁移到不同的云中是无缝的
- 开箱即用
    - 提供命令行工具以方便安装和使用
    - 集中定义规则
- 无侵入
    - 不依赖 Kubernetes 版本
    - 不依赖任何 CNI 或网络环境
    - 不需要修改现有环境
- 内网穿透
    - 只需要一个公共 IP
