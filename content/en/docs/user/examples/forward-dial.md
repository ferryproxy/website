---
title: "Forward Local Port to Cluster"
---

# Forward Local Port to Cluster

## Preparation

[Preparation](/docs/user/preparation)

## Forward Local Port to Cluster

    ferryctl local forward dial <local address port> <remote service port>

``` bash
ferryctl local forward dial 0.0.0.0:18080 web-0.test.svc:80
```

All accesses to port 127.0.0.1:18080 are forwarded to port web-0.test.svc:80

[Sample](https://github.com/ferryproxy/ferry/blob/main/test/test/test-forward.sh)
