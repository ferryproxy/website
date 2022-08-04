---
title: "预备工作"
---

## 下载 ferryctl

`ferryctl` 是 `Ferry` 的安装运维工具

需要为每个集群安装 `ferryctl`

https://github.com/ferryproxy/ferry/releases

## 安装 Tunnel

需要为每个集群安装 Tunnel

### 支持 LoadBalancer 的集群

如在各个公有云环境

``` bash
ferryctl data-plane init --tunnel-service-type=LoadBalancer
```

### 其他

如 Kind 或私有云环境

将默认使用 NodePort 暴露 31087 端口

``` bash
ferryctl data-plane init
```
