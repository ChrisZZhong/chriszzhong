---
layout: post
title: "Fault-Tolerance"
date: 2023-06-10
description: "Fault-Tolerance"
tag: Microservices
---

# Fault-Tolerance

## What is Fault-Tolerance?

Fault-tolerance is the property that enables a system to continue operating properly though there are some failures inside of it.

The more faults a system can tolerate without failing, the more fault-tolerant it is.

Fault-tolerance is an important feature of distrubuted systems.

## How to make microservices fault-tolerant?

### 1. Circuit Breaker

Circuit breakers can prevent repeated requests to a failing service, allowing it time to recover.

### 2. Timeout

Timeouts can prevent a service from waiting too long for a response from another service. Fail fast is better than waiting indefinitely.

### 3. Load Balancing

Use load balancers to distribute incoming requests evenly across multiple instances of a microservice. Load balancers can also detect and avoid routing traffic to unhealthy instances.
