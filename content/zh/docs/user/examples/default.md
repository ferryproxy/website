---
title: "默认示例"
---

# 默认示例

{{< hint info >}}
准备至少两个集群才能做演示

可以是一个节点的集群或者 Kind 起的集群但最少也要两个
{{< /hint >}}

<img src="/images/cloud-to-cloud.png" width="600">

## 下载 ferryctl

ferryctl 是 ferry 的安装运维工具

需要为每个集群的控制节点都安装一个 ferryctl

https://github.com/ferryproxy/ferry/releases

## 初始化控制面集群

``` bash
# 在控制面集群执行
ferryctl control-plane init
```

## 加入数据面集群

需要 3 步去配置

### 向控制面集群声明哪个数据面集群需要加入

``` bash
# 在控制面集群执行，预连接其他数据平集群
ferryctl control-plane join cluster-1
```

### 在数据面集群执行

上一个命令执行后, 会响应一个命令复制到数据面集群执行

### 在控制面集群执行

上一个命令执行后, 会响应一个命令复制到控制面集群执行

## 快速在本地拉起测试环境

要求: Docker, Kind, Go

``` bash
git clone https://github.com/ferryproxy/ferry
go install ./cmd/ferryctl
./test/hack/start-environment.sh default
```

将会使用 Kind 启动两个集群, 并在控制面集群安装好 ferry-controller, 但是没有配置路由规则

[环境状况](https://github.com/ferryproxy/ferry/blob/main/test/environments/default/)

在控制面集群配置路由规则

``` yaml
# 把 cluster-1 的 web-1.test.svc 映射到 control-plane 的 web-1.test.svc
# 把 control-plane 的 web-0.test.svc 映射到 cluster-1 的 web-0.test.svc
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
metadata:
  name: ferry-test
  namespace: ferry-system
spec:
  exports:
    - hubName: cluster-1
      service:
        namespace: test
        name: web-1
    - hubName: control-plane
      service:
        namespace: default
        name: web-0
  imports:
    - hubName: cluster-1
    - hubName: control-plane
```

[示例代码](https://github.com/ferryproxy/ferry/blob/main/test/test/test-in-both.sh)