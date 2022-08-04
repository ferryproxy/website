---
title: "Preparation"
---

## Download ferryctl

`ferryctl` is the installation and maintenance tool for `Ferry`

You need to install `ferryctl` for each cluster

https://github.com/ferryproxy/ferry/releases

## Install Tunnel

Tunnel needs to be installed for each cluster

### Clusters that support LoadBalancer

As in each public cloud environment

``` bash
ferryctl data-plane init --tunnel-service-type=LoadBalancer
```

### Other

such as Kind or private cloud environments

will use NodePort to expose port 31087 by default

``` bash
ferryctl data-plane init
```
