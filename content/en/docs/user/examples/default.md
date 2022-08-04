---
title: "Default Example"
---

# Default Example

{{< hint info >}}
Prepare at least two clusters for demonstration 

Can be a cluster of one node or a cluster of Kind but at least two.
{{< /hint >}}

<img src="/images/cloud-to-cloud.png" width="600">

## Download ferryctl

ferryctl is the installation and operation tool for ferry 

A ferryctl needs to be installed for each cluster's control node 

https://github.com/ferryproxy/ferry/releases

## Preparation

[Preparation](/docs/user/preparation)

## Join a Data Plane Cluster

### Define which Data Plane Cluster needs to be joined

``` bash
# execute on Control Plane Cluster
ferryctl control-plane join cluster-1
```

Need [handshake](/docs/user/handshake)

### Complete handshake

This data plane cluster can then be viewed in the control plane cluster

``` bash
kubectl get hub.traffic.ferryproxy.io -n ferry-system
```

## Quickly pull up a test environment locally

If you don't have a cluster to test and want to try it quickly, you can follow the process below

Requirement: Docker, Kind, Go

``` bash
git clone https://github.com/ferryproxy/ferry
go install ./cmd/ferryctl
./test/hack/start-environment.sh default
```

Two clusters will be started using Kind, and the ferry-controller will be installed in the Control Plane Cluster, but no routing rules will be configured

[Environment](https://github.com/ferryproxy/ferry/blob/main/test/environments/default/)

Configuration route rules

``` yaml
# Map cluster-1's web-1.test.svc to control-plane's web-1.test.svc
# Map control-plane's web-0.test.svc to cluster-1's web-0.test.svc
apiVersion: traffic.ferryproxy.io/v1alpha2
kind: RoutePolicy
metadata:
  name: ferry-test
  namespace: ferry-system
spec:
  exports:
    - hubName: cluster-1
      service:
        namespace: test
        name: web-1
    - hubName: control-plane
      service:
        namespace: test
        name: web-0
  imports:
    - hubName: cluster-1
    - hubName: control-plane
```

``` bash
# Go to the control-plane container and request the servuce mapped from cluster-1
kubectl --context=kind-ferry-test-control-plane exec -it svc/web-0 -n test -- wget -O - web-1
```

``` bash
# Go to the cluster-1 container and request the servuce mapped from control-plane
kubectl --context=kind-ferry-test-cluster-1 exec -it svc/web-1 -n test -- wget -O - web-0
```

[Sample](https://github.com/ferryproxy/ferry/blob/main/test/test/test-in-both.sh)
