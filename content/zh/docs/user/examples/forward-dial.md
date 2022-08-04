---
title: "转发本地端口到集群的端口"
---

# 转发本地端口到集群的端口

## 准备工作

[准备工作](/docs/user/preparation)

## 转发本地端口到集群的端口

    ferryctl local forward dial <local address port> <remote service port>

``` bash
ferryctl local forward dial 0.0.0.0:18080 web-0.test.svc:80
```

所有对 127.0.0.1:18080 端口的访问都会被转发到 web-0.test.svc:80 端口

[示例代码](https://github.com/ferryproxy/ferry/blob/main/test/test/test-forward.sh)
