---
title: "Manual Mapping Service"
---

# Manual Mapping Service

## Why this is needed

In some cluster unreachability scenarios, the apiserver address of the data plane needs to be exposed to the control plane in advance so that the control plane can access the apiserver of the data plane.

The routing rules configured by this feature are not controlled by the ferry-controller.

## Preparation

[Preparation](/docs/user/preparation)

## Manual Mapping Service

### Define exporting a service from another cluster

``` bash
ferryctl local manual import --reachable=true --tunnel-address=tunneladdress:31000 --export-service=web-1.test --import-service=web-1-8080.ferry-tunnel-system --port=8080
```

This command describes the mapping of the web-1.test.svc:8080 service of the export service cluster to the web-1-8080.ferry-tunnel-system:8080 service of the current cluster

    --tunnel-address The address of the Tunnel if the current cluster is reachable  
    --port The port of the service exported from the other cluster  
    --export-service Service exported from other cluster
    --import-service Mapping service created by the current cluster from services exported from other clusters 

Need [handshake](/docs/user/handshake)

## Quickly pull up a test environment locally

If you don't have a cluster to test and want to try it quickly, you can follow the process below

Requirement: Docker, Kind, Go

``` bash
git clone https://github.com/ferryproxy/ferry
go install ./cmd/ferryctl
./test/hack/start-environment.sh manual
```

The two clusters will be started using Kind, and the service routing rules between the two clusters will be configured

[Environment](https://github.com/ferryproxy/ferry/blob/main/test/environments/manual/)

[Sample](https://github.com/ferryproxy/ferry/blob/main/test/test/test-manual.sh)
