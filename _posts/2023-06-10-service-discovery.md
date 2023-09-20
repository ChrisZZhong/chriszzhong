---
layout: post
title: "Service Discovery & microservices communicate"
date: 2023-06-10
description: "Service Discovery"
tag: Microservices
---

# Service Discovery

## How do microservices communicate?

### HTTP Requests

Microservices communicate with each other using HTTP requests. Each microservice has its own REST API. In Spring Boot, we can use the `RestTemplate` class to make HTTP requests.

### Eureka and Feign

`Eureka` is a service discovery tool. It allows microservices to register themselves and discover other services. Each service send a heartbeat to Eureka to let it know that it is still alive. If Eureka does not receive a heartbeat from a service, it will remove it from its registry.

`Feign` is a REST client to make HTTP requests to other microservices without using `RestTemplate`. It uses Eureka to discover other services. In this way, we can make HTTP requests to other services without hardcoding the URL, also simplifying the code.

### Message Brokers

We can use a `message broker` like `RabbitMQ` or `Kafka` to send messages between microservices to communicate `Asychonously`.

For example, when a user creates a new account, we can send a message to the email service to send a welcome email and to the notification service to send a notification to the user.
