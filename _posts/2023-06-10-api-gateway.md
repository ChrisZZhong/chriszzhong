---
layout: post
title: "API GateWay"
date: 2023-06-10
description: "API GateWay"
tag: Microservices
---

# API GateWay

## Why do we need API Gateway?

API Gateway is a `single entry point` for all the microservices.

`Route requests` This is convient for frontend developers to make requests to a single endpoint. The API Gateway will route the request to the appropriate microservice.

```
API gateway handles requests in one of two ways:
1.Some requests are simply proxied/routed to the appropriate service
2. handles other requests by fanning out to multiple services.
```

`Authentication` The API Gateway can handle authentication for all the microservices.

`Load Balancing` The API Gateway can handle load balancing requests to the microservices.

## Is gateway necessary?

`No, it is not necessary`. You can make requests directly to the microservices. However, it is not good for decoupling. If you make requests directly to the microservices, you will have to change the frontend code if you change the microservices. If you use API Gateway, you can change the microservices without changing the frontend code.
