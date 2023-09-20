---
layout: post
title: "Solid Principle"
date: 2023-03-29
description: "Solid Principle"
tag: Java Core
---
# Solid Principle

## Single Responsibility Principle

- **A class should have one and only one reason to change, meaning that a class should have only one job.**

  **Example:**  
  Suppose you have a shape class, like triangle, you want to have a method to give you the area of the shape, instead of writing a method called calculateArea, you should create a new class called areaCalculator which is responsible for calculating area of all types, and call areaCalculator when you need to calculate the area.

## Open-Closed Principle

- **Objects or entities should be open for extension but closed for modification.**

  **Example:**  
   you have different payment methods, like card, cash, third parties, instead of checking input several times with if else statement, you should generate a new interface like payProcessor to handle the payment, this is good for decoupling. You don’t have to modify this class when a new payment method is added, all you need to do is generate a new class and extend the payProcessor.

## Liskov Substitution Principle

- **Every subclass/derived class should be substitutable for their base/parent class.**

  **Example:**  
   List and arrayList are both list, so you can use arrayList anywhere you use list.

## Interface Segregation Principle

- **A client should never be forced to implement an interface that it doesn’t use**

  **Example:**  
   Take payment as mentioned above as an example, A and B both implement payProcessor, A have charge and refund function, suppose B do not support refund, but B have to implement an empty method, this is a violation. Instead, we should separate the parProcessor to chargeProcessor, refundProcessor.

## Dependency Inversion Principle

- **The high-level module must not depend on the low-level module, but they should depend on abstractions.**

  **Example:**  
   Still use payment as an example, if you want to use a new payment method, you should not modify the payProcessor, instead, you should create a new class and extend the payProcessor, and use the new class to handle the new payment method.
