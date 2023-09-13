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

`Logging` is used to record the events that happen in our application. It is used to debug and monitor the application. Spring Boot uses `Logback` as the default logging framework.
Also we can use `Log4j2`.

Log4j is vulnerable to `Log4Shell` attack. So we should use Log4j2 instead.

Log Level: `ERROR`, `WARN`, `INFO`, `DEBUG`, or `TRACE`
