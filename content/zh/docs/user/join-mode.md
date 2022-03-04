---
title: "Join Mode"
---

# 加入模式

``` console
> ferryctl control-plane pre-join --help
Generate command for data plane join
Need to copy the generated command to run on the data plane.

Usage:
  ferryctl control-plane pre-join [command]

Aliases:
  pre-join, p, pj, join, j

Available Commands:
  direct      Clusters can reach each other
  tunnel      Control plane can't touch the data plane

Flags:
  -h, --help                                  help for pre-join
```
当前有两种加入方式

1. direct
2. tunnel

## direct

适用于集群之间网络是互通的情况,
不需要做穿透或者代理操作.


## tunnel

适用于控制面集群无法访问到数据面集群但是数据面集群可以访问控制面集群的情况,
这时需要建立控制面集群到数据面集群的内网穿透.
