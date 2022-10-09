---
title: "Route"
---

# Route

Route CR 定义 Hub 之间的单个 Service 的路由规则

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: Route
metadata:
  name: route-name
  namespace: ferry-system
spec:
  export:
    hubName: cluster-1
    service:
      namespace: default
      name: app-1
  import:
    hubName: cluster-0
    service:
      namespace: default
      name: app-1
```

示例的 CR 描述了 Hub cluster-1 导出 Service app-1.default, 在 Hub cluster-0 导入它并命名为 app-1.default
导入和导出的 name 和 namespace 不必一样

