---
title: "Hub"
---

# Hub

Hub CR 定义一个 Hub, 是与其他 Hub 通信地址,
现在只支持一个集群, 未来会添加支持任何可能得设备作为 Hub, 甚至是你的笔记本也行

Hub 为 [RoutePolicy CR][1] 和 [Route CR][2] 提供了计算的依据

``` yaml
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: Hub
spec:
  gateway:
    # 表示这个 Hub 是否是可以被连接的
    reachable: true

    # 在 reachable 为 true 时, 其他 Hub 会根据这个地址连接本 Hub
    address: 1.1.1.1:31087

    # 这是一个 Hub 名的列表，本 Hub 需要通过它来到达其他 Hub 使用
    # 被 RoutePolicy 用来计算 Route
    navigationWay:
      - hubName: hubname

    # 这是一个 Hub 名的列表，其他 Hub 需要通过它达到本 Hub
    # 被 RoutePolicy 用来计算 Route
    receptionWay:
      - hubName: hubname

    # 是一个代理的列表，这个 Hub 要到达其他 Hub 必须通过这个代理。
    # 当此 Hub 到达其他 Hub 时使用
    navigationProxy:
      - proxy: hubname

    # 是一个代理的列表，其他 Hub 到达到本 Hub 达必须通过这个代理。
    # 当此 Hub 到达其他 Hub 时使用
    receptionProxy:
      - proxy: hubname
```

[1]: ./route_policy
[2]: ./hub
