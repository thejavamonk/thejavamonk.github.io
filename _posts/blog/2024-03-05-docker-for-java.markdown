---
layout: post
title: "Docker for Java Developers"
date: 2024-03-05
categories: blog
tags: docker containerization
---

Docker has revolutionized the way we develop and deploy applications. Learn how to containerize your Java applications for consistent environments.

## Creating a Dockerfile

{% highlight dockerfile %}
FROM openjdk:11-jre-slim
WORKDIR /app
COPY target/app.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
{% endhighlight %}

## Docker Compose

Use Docker Compose to run multiple containers together:

{% highlight yaml %}
version: '3'
services:
  app:
    build: .
    ports:
      - "8080:8080"
  db:
    image: postgres:latest
    environment:
      POSTGRES_PASSWORD: password
{% endhighlight %}

Docker simplifies deployment and ensures consistency across different environments.
