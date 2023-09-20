---
layout: post
title: "Dependency injection"
date: 2023-04-06
description: "Dependency injection"
tag: Spring Framework
---
# Dependency injection

## What is dependency injection?

Dependency injection is an implementation of IoC principle (invert the control of the object creation to the spring framework) to achieve loose coupling. It is the main advantage of Spring framework. It makes the code more extendable.

### Three types of dependency injection

Use `@Autowired` to inject dependency, Setter injection is recommended.

1. `constructor` injection
2. `Setter` injection  
   make setter injection mandatory: @Required, recently recommend constructor
3. `Field` injection

### Circular dependency

Constructor injection sometimes causes circular dependency, the field injection cannot be injected to the immutable class, and it is tight coupling.

### Dependency ambiguity

If there are multiple beans that implement the same interface, the container will not know which one to inject, We can use `@Primary` to determine which bean has higher priority, or use `@Qualifier` to specify an exact bean

## Two types of IOC containers

1. `BeanFactory`

   BeanFactory is `lazy loaded`, beans are loaded on-demand. BeanFactory only supports `XML` based configuration.

2. `ApplicationContext`

   ApplicationContext extends the `BeanFactory` interface, It is `eager loaded`, that is, beans are loaded on start-up. ApplicationContext supports both `XML and annotation` based configuration. In spring boot we generally use Application Context as the IOC container

## IOC container life cycle

1. When Spring application starts, IOC container is instantiated(BeanFactory or Application Context)

2. IOC container read the bean class from config files such as XML or annotations like @ComponentScan

3. Create bean instance based on the Bean definition

4. When a bean is required, inject the required dependencies.

5. Post-Post-initialization Pre-destruction and bean call back will be executed, then is the bean destruction when spring application shut down, then the container will shut down.
