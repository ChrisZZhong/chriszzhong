---
layout: post
title: "Spring Boot"
date: 2023-04-07
description: "Spring Boot"
tag: Spring Framework
---
# Spring Boot

## Spring Boot VS Spring Framework

Spring framework provides a comprehensive programming and configuration model for Java based applications, It integrates well with a lot of components like IOC, AOP, JDBC, ORM, security.

MVC architecture, which is model view and controller is for web applications. It has predefined templates to connect to the database, it achieves loose coupling through the dependency injection.

One of the cons is that the configuration of the spring framework is very complex, you have to write a huge amount of XML files which greatly slows down development. For example, you should manually put the bean objects in the approties.xml file, for Mybatis, you should manually write sql and map the result to the pojo class.To solve this problem, the sun company, the owner of the spring, gave a solution, Spring Boot.

Spring Boot is a framework that is built on top of Spring Framework, it uses starter dependencies and enables annotation based configuration (that is auto config) which greatly reduces the time for setting up configurations.

## Auto Configuration @SpringBootApplication

The entry point of every spring boot application is the class annotated with the `@SpringBootApplication`

It contains three annotation

- `@EnableAutoConfiguration` : Allows auto configuration based on the .jar dependencies in the pom.xml file

- `@ComponentScan` : scan the `@Component` under the basic folder.

- `@Configuration` : allows us to register extra beans in the context or annotate additional configuration classes
