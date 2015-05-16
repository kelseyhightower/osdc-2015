# Building Distributed Systems with CoreOS

[Open Source Data Center Conference 2015 Berlin](https://www.netways.de/index.php?id=2561&L=1)    
Wednesday, April 22nd, 2015
12:00 - 1:00 pm

## Slides

This talk requires the [Go Present](https://godoc.org/golang.org/x/tools/present) tool to view locally, or just view the slides [online](http://go-talks.appspot.com/github.com/kelseyhightower/osdc-2015/slides/building-distributed-systems-with-coreos.slide).

## Video

Recorded video is available on [Youtube](https://www.youtube.com/watch?v=bU9Uh4ihgR4&feature=youtu.be)

## Abstract

Building distributed systems is hard, but with the right components just about anyone can get started. At the heart of any distributed system is the underlying infrastructure, which often includes a collection of servers, a central configuration and lock service, and a scheduler to manage your workloads.

CoreOS provides all of these components starting with the base OS, CoreOS Linux; a minimal OS optimized for running Linux containers such as Rocket and Docker. Next is the central key value store, etcd, which provides shared configuration, service discovery, and a cluster wide lock service built on top of the Raft consensus algorithm for high-availability. Finally, fleet is a distributed init system that ties it all together and provides low level workload scheduling. fleet is often used to install higher level workload distribution systems such as Mesos or Kubernetes.

All of these projects are open source and part of growing community. Come learn how they work and how you can get involved.
