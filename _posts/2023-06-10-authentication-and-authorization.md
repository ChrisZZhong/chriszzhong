---
layout: post
title: "Authentication-and-Authorization"
date: 2023-06-10
description: "Authentication-and-Authorization"
tag: Microservices
---

# user Authorization in mocroservices

## 1. Single Sign on

### what is SSO

**Single sign-on (SSO) allows the user to access multiple services without having to authenticate more than once.**

This is achieved by storing the user's authentication information in a trusted service, called the **identity provider** (IdP). The identity provider is then used to authenticate the user to other services, called **service providers** (SP).

#### 1.1. OAuth2

OAuth 2.0 is the industry-standard protocol for authorization. OAuth 2.0 supersedes the work done on the original OAuth protocol created in 2006. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices. This specification and its extensions are being developed within the IETF OAuth Working Group.
