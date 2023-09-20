---
layout: post
title: "Spring Cloud Config"
date: 2023-06-10
description: "Spring Cloud Config"
tag: Microservices
---

# Spring Cloud Config

## Where do you store your configuration file when you use microservices?

### Spring Cloud Config is a centralized place to store the configuration file for all microservices.

- In a monolithic application, we can store the configuration file in the `resources` folder.

- In a microservice application, we can store the configuration file in the `resources` folder of each microservice. However, this is not a good idea because we have to update the configuration file in each microservice when we want to change the configuration file.

- We can store the configuration file in a centralized place. So we need Spring Cloud Config.

## How to use Spring Cloud Config in Spring Boot?

To Create a server:

1. Set up configuration repo: choose a version control system like Git and create a new repo to store the config
2. Create a Spring Boot application and add spring-cloud-config-server dependencies.
3. Add `@EnableConfigServer` annotation to the main class.
4. Add `application.properties` file and set up the port and the config repo url.

To Create a client:

1. Create a Spring Boot application and add spring-cloud-starter-config dependencies.
2. Add `bootstrap.properties` file and set up the port and the config server url.
3. Add `@RefreshScope` annotation to the main class.
4. Add `@Value("${property.name}")` annotation to the field that you want to inject the value from the config server.
