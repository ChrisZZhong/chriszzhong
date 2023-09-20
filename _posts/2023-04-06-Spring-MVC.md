---
layout: post
title: "Spring MVC"
date: 2023-04-06
description: "Spring MVC"
tag: Spring Framework
---
# Spring MVC

## What is Spring MVC?

Spring MVC is a framework built on top of the Spring framework, it is a web framework that is used to build web applications. It is based on the MVC architecture, which is `model` `view` and `controller`.

`Model` is the data layer, it is used to store the data, it is usually a POJO class.

`View` is the presentation layer, it is used to display the data, it is usually a JSP page.

`Controller` is the business layer, it is used to process the data, it is usually a servlet.

## workflow

Spring MVC has a central controller called DispatcherServlet, which provides a shared algorithm for request processing. Dispatcher Servlet receives all of the HTTP requests and maps them to controller classes. Dispatcher Servlet first unifies the request processing. After enriching and dispatching the request, Dispatcher Servlet handles the request and processes arguments and returns values via controller. Finally, Dispatcher Servlet renders the view.

To find the handler that matches the request, Spring goes through the registered implementations of the HandlerMapping interface, uses HandlerMapping and HandlerAdapter components. Generally use @RequestMapping to map the controller and methods.

1. The user sends a request to the front controller (DispatcherServlet).

2. The front controller (DispatcherServlet) sends the request to the handler mapping.

3. The handler mapping sends the request to the controller.

4. The controller processes the request and sends the request to the model.

5. The model processes the request and sends the request to the view.

6. The view processes the request and sends the request to the front controller (DispatcherServlet).

7. The front controller (DispatcherServlet) sends the request to the view resolver.

8. The view resolver sends the request to the view.

9. The view processes the request and sends the response to the front controller (DispatcherServlet).

10. The front controller (DispatcherServlet) sends the response to the user.

## View Resolver

View Resolver is used to map the view name to the actual view. It enables us to render models in the browser without tying the implementation to specific view technology.
