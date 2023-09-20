---
layout: post
title: "Cascading Failure"
date: 2023-06-10
description: "Cascading Failure"
tag: Microservices
---

# Cascading Failure

## What is Cascading Failure?

Cascading failure is a failure that spreads across multiple systems, causing a chain reaction of failures. It is a common problem in distributed systems and can be caused by server overload, software bugs, or network issues.

## How to prevent Cascading Failure?

### Circuit Breaker

`Circuit breaker` is a design pattern that can be used to prevent cascading failures and enhance the fault tolerance of the system.

Every method call is wrapped in a circuit breaker object, the circuit breaker then monitors the services for failures. Once the service `reaches a certain failure threshold`, the circuit breaker triggers, and all further calls to the target service return with an error, without the method call being made at all.

---

It has three states: **`Closed`**, **`Open`**, **`Half-Open`**

**`Closed`** : In the closed state, the circuit breaker allows requests to pass through to the external service or resource.

**`Open`**: Once the service reaches a certain failure threshold, the circuit breaker triggers, and all further calls to the target service return with an error, without the method call being made at all.

**`Half-Open`** : After a predefined period of time, the circuit breaker transitions to the half-open state, allowing a limited number of test requests to pass through to check if the external service or resource has recovered. If these test requests succeed, the circuit breaker transitions back to the closed state. If they fail, it returns to the open state.

<img src = "/images/Full-Stack/Microservices/circuit-breaker.png">
