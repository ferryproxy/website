---
title: "Forward Service to Local Port"
---

# Forward Service to Local Port

## Installing Tunnel in the cluster

``` bash
ferryctl data-plane init
```

## Forward Service to Local Port

    ferryctl local forward listen <remote service port> <local address port>

``` bash
ferryctl local forward listen local.test.svc:80 127.0.0.1:28080
```

All accesses on web-0.test.svc:80 in the cluster are forwarded to the local port 127.0.0.1:28080

[Sample](https://github.com/ferryproxy/ferry/blob/main/test/test/test-forward.sh)
