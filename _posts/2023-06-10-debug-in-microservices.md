---
layout: post
title: "Debug in Microservices"
date: 2023-06-10
description: "Debug in Microservices"
tag: Microservices
---

# Debug in Microservices

## How to troubleshoot when there is an error in the microservice application?

### Log

We can use `Log` to quickly narrow down the space of the error. During development, we can save the log to the local file. If error happens, we can check the log file.

We can also use `Spring Boot Actuator` to monitor the application. It provides a set of `HTTP endpoints` to monitor the application. For example, `Auditing`, `health`, and `metrics gathering`.

### Distributed Tracing

`Distributed Tracing` is used to track the request flow across the microservices. If error happens, the distributed tracing can help us to find out which microservice is the root cause.

```Java
Class TraceId {
    String id;
    String parentId;
    String spanId;
    String traceId;
    String name;
    String timestamp;
    String duration;
    String localEndpoint;
    String remoteEndpoint;
    String tags;
    String annotations;
    String debug;
    String shared;
}
```
