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

需要 3 步去配置

### 定义从其他集群导出某一服务

``` bash
ferryctl local manual import --reachable=true "--tunnel-address=${HOST_IP}:31000" --export-host-port=web-1.test.svc:8080 --import-service-name=web-1-8080
```

这条命令描述将导出服务集群的 web-1.test.svc:8080 服务映射到当前集群的 web-1-8080.ferry-tunnel-system:8080 服务

    --reachable=true 当前集群是否可以达到  
    --tunnel-address 当前集群如果可以达到的情况下 Tunnel 的地址  
    --export-host-port 从其他集群导出的服务端口  
    --import-service-name 当前集群从其他集群导出的服务建立的映射服务 (默认在 ferry-tunnel-system 命名空间下)  

### 导出服务的集群执行

上一个命令执行后, 会响应一个命令复制到导出集群执行

### 导入服务的集群执行

上一个命令执行后, 会响应一个命令复制到导入集群执行

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
