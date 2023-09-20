---
layout: post
title: "Application Monitoring (Actuator & Logging)"
date: 2023-06-10
description: "Application Monitoring (Actuator & Logging)"
tag: Microservices
---

# Application Monitoring

## How to monitor an Spring Boot application?

### Actuator

Spring Boot `Actuator` is used to monitor the status of the application in real time. It provides a set of `HTTP endpoints` to monitor the application. For example, `Auditing`, `health`, and `metrics gathering`.

#### How to enable Actuator?

To enable Actuator, we need to add the `spring-boot-starter-actuator` dependency.

predefined endpoints:

- /health : summaries the health status of our application
- /info : displays general application info
- /beans : displays a complete list of all the Spring beans in our application

---

### Logging

`Logging` is used to record the events that happen in our application. It is used to debug and monitor the application.

For logging, Spring Boot uses `Logback` by default, so the console shows the date and time, log level, process ID, thread name, logger name and the log message. To configure it, put a file named logback.xml under the resources folder so the spring boot will automatically load it.

Also we can use `Log4j2`. `Log4j` is vulnerable to `Log4Shell` attack. So we should use `Log4j2` instead.

#### Log Levels:

Log Level: `ERROR`, `WARN`, `INFO`, `DEBUG`, or `TRACE`

`INFO` : log informational messages that provide general details about the application's execution. Include include startup messages, successful request handling

`WARN` : log warning messages indicate potential issues may cause critical errors

`ERROR` : log error messages that indicate failures, exceptions, or critical issues within the application.
