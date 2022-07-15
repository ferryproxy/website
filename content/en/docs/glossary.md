---
title: "Glossary"
---

# Glossary

## API server  
  Also known as:kube-apiserver  
  The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane

## Cluster  
  A set of worker machines, called nodes, that run containerized applications. Every cluster has at least one worker node.

## Controller  
  In Kubernetes, controllers are control loops that watch the state of your cluster, then make or request changes where needed. Each controller tries to move the current cluster state closer to the desired state.  
  Controllers watch the shared state of your cluster through the apiserver (part of the Control Plane).

## Control Plane  
  In Kubernetes, the container orchestration layer that exposes the API and interfaces to define, deploy, and manage the lifecycle of containers.  
  This layer is composed by many different components, such as (but not restricted to):
    - Etcd
    - API Server
    - Scheduler
    - Controller Manager

## Control Plane Cluster  
  In a multi-Kubernetes cluster, the Control Plane Cluster is to provide control plane services to other clusters.

## Data Plane  
  In Kubernetes, the layer that provides capacity such as CPU, memory, network, and storage so that the containers can run and connect to a network.

## Data Plane Cluster  
  In a multi-Kubernetes cluster, the Data Plane Cluster works primarily on its own services.

## Ferryctl  
  A tool for installing and maintaining Ferry

## Ferry Controller  
  It is the controller of Ferry for pushing Service route rules, and to dynamically discover the Service that needs to be mapped.  
  Requires installation in Control Plane Clusters

## Ferry Tunnel  
  It is the tunnel of Ferry for route the Service from one cluster to another.  
  Requires installation in Data Plane Clusters
