# kubernetes-goldengate
Deploy an Oracle Golden Gate Free 23c instance on kubernetes.

## Table of contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Upgrade](#upgrade)

## Introduction
The availability of new Oracle Golden Gate 23c free has been announced, which takes advantage of the new GoldenGate Microservice 23.3 as its primary engine.

Oracle GoldenGate 23c Free is the same robust Oracle GoldenGate on which enterprises worldwide rely. It provides a complete experience and is packaged for user-friendliness and straightforward download—for free.

GoldenGate Free offers built-in support for low-latency replication, modern data types, microservices, and all the top-tier GoldenGate features, all in a single, user-friendly, easy to setup free application.

In addition to the previously available uni-direction replication from earlier releases, this most recent version of GoldenGate 23c adds support for Oracle Database 23c and introduces a completely new, significantly simplified user interface for configuring multi-active data replication with Automatic Conflict Detection and Resolution (ACDR).

GoldenGate Free is completely free, and its pre-built container is simple to acquire from the Oracle Container Registry, and the container can run on environments such as Podman, Rancher, or Docker.  You can visit the Oracle Container Registry, download and review notes by visiting: http://bit.ly/oggcr

This repository helps you to deploy GoldenGate Free in a k8s cluster

## Prerequisites
A running kubernetes cluster is needed to deploy Golden Gate 23c Free. Check [deploy-kubernetes-cluster](https://github.com/hfolguera/deploy-kubernetes-cluster) repository to deploy the required k8s cluster.
In my case, I'm using MetalLB as Load Balancer.

## Installation
Follow the next steps to deploy Oracle Golden Gate 23c Free:

### Create namespace
```
kubectl apply -f goldengate-namespace.yaml
```

### Create secret
**Remember to change the password!**
```
kubectl create secret generic oggadmin --from-literal=ogg_admin_pwd='xBvPi72VwW/r-WYzD' -n goldengate
```

### Create deployment
```
kubectl apply -f goldengate-deployment.yaml
```

### Create service
```
kubectl apply -f goldengate-service.yaml
```

## Upgrade
#TODO

