---
title: "创建并转发集群的 Service 端口到本地端口"
---

# 创建并转发集群的 Service 端口到本地端口

## 准备工作

[准备工作](/docs/user/preparation)

## 创建并转发集群的 Service 端口到本地端口

    ferryctl local forward listen <remote service port> <local address port>

``` bash
ferryctl local forward listen local.test.svc:80 127.0.0.1:28080
```

所有在集群里 web-0.test.svc:80 端口的访问都会被转发到本地的 127.0.0.1:28080 端口

[示例代码](https://github.com/ferryproxy/ferry/blob/main/test/test/test-forward.sh)
