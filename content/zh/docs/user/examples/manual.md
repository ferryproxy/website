---
title: "手动映射服务"
---

# 手动映射服务

## 为什么需要这个

在某些集群不可达的场景里, 需要提前暴露数据面的 apiserver 地址给控制面, 这样控制面就可以访问数据面的 apiserver

由该功能配置的路由规则不受 ferry-controller 的控制

## 准备工作

[准备工作](/docs/user/preparation)

## 手动映射服务

### 定义从其他集群导出某一服务

``` bash
ferryctl local manual import --reachable=true --tunnel-address=tunneladdress:31000 --export-service=web-1.test --import-service=web-1-8080.ferry-tunnel-system --port=8080
```

这条命令描述将导出服务集群的 web-1.test.svc:8080 服务映射到当前集群的 web-1-8080.ferry-tunnel-system:8080 服务

    --tunnel-address 当前集群如果可以达到的情况下 Tunnel 的地址  
    --port 从其他集群导出的服务端口  
    --export-service 从其他集群导出的服务
    --import-service 当前集群从其他集群导出的服务建立的映射服务 

需要[握手](/docs/user/handshake)

## 快速在本地拉起测试环境

如果你没有可以测试集群又想快速尝试可以按照下面的流程

要求: Docker, Kind, Go

``` bash
git clone https://github.com/ferryproxy/ferry
go install ./cmd/ferryctl
./test/hack/start-environment.sh manual
```

将会使用 Kind 启动两个集群, 并配置好两个集群之间的服务路由规则

[环境状况](https://github.com/ferryproxy/ferry/blob/main/test/environments/manual/)

[示例代码](https://github.com/ferryproxy/ferry/blob/main/test/test/test-manual.sh)
