---
title: "术语"
---

# 术语

## API server  
  也被称为: kube-apiserver  
  API服务器是 Kubernetes 控制平面的一个组件，它暴露了 Kubernetes 的 API。API Server 是 Kubernetes 控制平面的前端。

## Cluster  
  也被称为: 集群  
  一个机器，称为节点，运行容器化应用程序。每个集群至少有一个节点。

## Controller  
  也被称为: 控制器  
  在 Kubernetes 中，控制器是观察集群状态的控制回路，然后在需要时进行或请求改变。每个控制器都试图使当前的集群状态更接近理想状态。 
  控制器通过 apiserver（控制平面的一部分）观察集群的共享状态。

## Control Plane  
  也被称为: 控制面  
  在 Kubernetes 中，中容器协调层，暴露了定义、部署和管理容器生命周期的API和接口。  
  该层由许多不同的组件组成，例如（但不限于）。
    - Etcd
    - API Server
    - Scheduler
    - Controller Manager

## Control Plane Cluster  
  也被称为: 控制面集群  
  在多 Kubernetes 集群中，控制平面集群要向其他集群提供控制平面服务。

## Data Plane  
  也被称为: 数据面  
  在 Kubernetes 中，中提供CPU、内存、网络和存储等容量的层，以便容器能够运行并连接到网络。

## Data Plane Cluster  
  也被称为: 数据面集群  
  在多 Kubernetes 集群中, 数据面集群主要工作是自身的服务。 

## Ferryctl  
  一个用于安装和维护 Ferry 的工具。 

## Ferry-Controller  
  它是 Ferry 的控制器，用于推送服务路由规则，并动态地发现需要映射的服务。 
  需要安装在控制平面集群中

## Ferry-Tunnel  
  它是 Ferry 的隧道，用于服务从一个集群路由到另一个集群。 
  需要安装在数据平面集群中

