---
title: "Route Policy"
---

# Route Policy

RoutePolicy 是用于定义通用的复合型的路由规则, 最终会转换成 [Route CR][1]

## 明确路由
### 单对单导入

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
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
这是一个和 [Route CR][1] 的示例等价的 CR

### 从多个 Hub 导入

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-1
      service:
        namespace: default
        name: app-1
    - hubName: cluster-2
      service:
        namespace: default
        name: app-1
  imports:
    - hubName: cluster-0
      service:
        namespace: default
        name: app-1
```

这个路由规则会生成两条 [Route CR][1], 
分别是把 [Hub][2] cluster-2 和 cluster-2 的 app-1.default 导入 [Hub][2] cluster-0 
这是会在 cluster-0 的 app-1.default 的 endpoint 配置多个 backend 分别指向导入的两条路由

就算是写在不同的 RoutePolicy CR 或者 [Route CR][1] 中, 只要其导入的目的地是一样的都会为 endpoint 配置多个 backend

### 导出到多个 Hub

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-0
      service:
        namespace: default
        name: app-1
  imports:
    - hubName: cluster-1
      service:
        namespace: default
        name: app-1
    - hubName: cluster-2
      service:
        namespace: default
        name: app-1
```

这条规则其实等价于两条单对单的规则

## 匹配的路由

除了明确的路由之外, Ferry 提供了 label 筛选需要导入导出 Service 的能力
不过要注意的是匹配路由不能修改导入的 name

### 使用 Label 筛选的批量导出
``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-1
      service:
        labels:
          export: enabled
        namespace: default
  imports:
    - hubName: cluster-0
```

这条路由规则将会在 [Hub][2] cluster-1 的 namespace default 中匹配所有带有 `export=enabled` label 的 Service 导出到 [Hub][2] cluster-0

### 使用 Label 筛选的批量导入
``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
spec:
  exports:
    - hubName: cluster-1
      service:
        labels:
          export: enabled
        namespace: default
  imports:
    - hubName: cluster-0
      service:
        labels:
          export-2: enabled
```

这条规则在上一条的基础上增加了导出的 Service 必须还带有 `export-2=enabled` label

[1]: ./route
[2]: ./hub