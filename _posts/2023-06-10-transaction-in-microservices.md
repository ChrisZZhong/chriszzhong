---
layout: post
title: "Transaction in microservices"
date: 2023-06-10
description: "Transaction in microservices"
tag: Microservices
---

# Transaction in microservices

## 2-phase commit

`2-phase commit` is a widely used pattern to implement distributed transaction management.

<img src = "/images/Full-Stack/Microservices/2-phase-commit.png">

It has two phases:

1. `Prepare phase`: The coordinator asks the participating nodes whether they are ready to commit.

2. `Commit phase`: If all participating nodes are ready, the coordinator will ask them to commit their changes, or roll back if at least one node failed

### Downside

- Everything depends on the coordinator, so it can be a single point of failure. If the coordinator fails, the whole transaction fails.

- All other services need to wait for the slower services to finish their confirmation, so the overall performance depends on the slower service.

- 2PC protocol relies on the ACID principles to work, and since NoSQL database generally do not support ACID, so if one of your microservices uses NoSQL, 2pc won’t work for that particular service, and the entire microservices family cannot work.

## SAGA

The `Saga Pattern` is a crucial design pattern used in distributed systems and microservices architectures to effectively `manage complex and long-running transactions` while `ensuring data consistency`. It addresses the challenges that arise when multiple services need to collaborate in a transactional process, particularly in scenarios where a traditional two-phase commit (2PC) approach isn't practical or efficient.

<img src = "/images/Full-Stack/Microservices/Saga-design-pattern.png">

### How it works

- The SAGA Execution Coordinator is the central component to implement the previous SAGA Flow.

- Each service in the saga is responsible for its own transaction and publishes events to trigger the next service in the saga.

- The SEC contains a SAGA log that captures the sequence of events of a distributed transaction.

- For any failure, the SEC inspects the Saga
  log to identify the impacted components and the sequence in which the compensating transactions should run.

### Two types of SAGA

- `Choreography-based SAGA`: Each service publishes events to trigger the next service in the saga. This is the most common approach.

- `Orchestration-based SAGA`: A central component (the orchestrator) is responsible for determining the sequence of service invocations and for forwarding the necessary data to each service.

## What is Event Driven development?

`Event-driven development` : Instead of sending HTTP requests to other services to ask for
information, now we have the services send information out as
“events” as they become ready to other services.

- Requires an intermediary, in our case we are using the message broker Kafka to store the “event” messages.

<img src = "/images/Full-Stack/Microservices/SAGA-Choreography-kafka.png">

<img src = "/images/Full-Stack/Microservices/Spring-WebFlux.png">
