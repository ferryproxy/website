---
title: "Handshake"
---

# handshake

Some commands need to notify both clusters of this behavior called handshaking

## Automatic

If two clusters can be connected at the same time

`KUBECONFIG` specifies the kubeconfig file for the current cluster

`FERRY_PEER_KUBECONFIG` specifies the kubeconfig file of the peer cluster

## Manual

If you cannot connect to both clusters at the same time

### First response

After the command is executed in the current cluster, a response is copied to the peer cluster to execution

### Second response

After the command is executed in the peer cluster, a command is copied to the current cluster to execution
