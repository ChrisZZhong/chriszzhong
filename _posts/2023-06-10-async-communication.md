---
layout: post
title: "Async (@Async & messaging)"
date: 2023-06-10
description: "Async (@Async & messaging)"
tag: Microservices
---

# Async (@Async & messaging)

## Async programming

**Example: suppose prepare the home page, we need 4 independent calls - userInfo(2s), AccountInfo(4s), BillingInfo(1s), UsageInfo(5s). If we execute synchoronously, we have to wait 12s, If we use Async, we only need to wait 5s.**

### @Async

`@Async` annotation is used to mark that method should run in a separate thread async. To get start, need to add `@EnableAsync` to either `@Configuration` class or `@SpringBootApplication` class.

By default, Spring uses `SimpleAsyncTaskExecutor` to run methods async. We can override the default at:  
`Application level`: choose different `TaskExecutor` or create a custom one.  
`Method level`: use `@Async("customExecutor")` to specify the executor to use.

### ExecutorService

`ExecutorService` is an interface used to deal with the threads. It can run multiple tasks and manage a thread pool, we don't need to manually create a thread.

Besides taking `Runnable` and `callable` interface, it can also accept `CompletableFuture` to run asynchronous tasks.

## Message Queue (RabbitMQ, Kafka)

**when a user submits a time-consuming task (like generating a report or processing an image), the web application can send a message to RabbitMQ to handle the task asynchronously. This way, the user doesn't have to wait for the task to complete**

### RabbitMQ

RabbitMQ is a message broker: it accepts and forwards messages. sender can send message to the queue, and receiver can get message from the queue. It's a middleman between sender and receiver.

#### Three components of RabbitMQ

- `Exchange`: a message router, it receives messages from producer and pushes them to queues based on the `Binding`.

- `Queue`: place that stores messages, it follows `FIFO`.

- `Binding`: a link between exchange and queue. An exchange will use these bindings to route messages to queues

#### Four types of exchange

- `Direct exchange`: a message goes to the queues whose binding key exactly matches the routing key of the message.

- `Fanout exchange`: a message goes to all queues bound to the exchange.

- `Topic exchange`: a message goes to the queues whose binding key matches the routing key of the message. The binding key can use wildcard.

- `Headers exchange`: a message goes to the queues whose headers matches the headers of the message.

#### dead letter exchange (DLX)

When a message is rejected or expired, it will be sent to a dead letter exchange. The dead letter exchange will route the message to a dead letter queue. The dead letter queue can be used to store the messages that can't be processed.
