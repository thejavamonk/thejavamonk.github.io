---
layout: post
title:  "OutOfMemory"
date:   2016-05-08
categories: blog
tags: java
---

Some common jargons to know about before starting to debug the OutOfMemory Issue:

Head Dump:

A heap dump is a complete view of the entire heap, i.e. all objects that have been created with new. If you're running out of memory then this will be rather large. It shows you how many of each type of object you have.

Thread Dump:

A thread dump shows you the stack for each thread, showing you where in the code each thread is at the time of the dump. Remember that any thread could have caused the JVM to run out of memory but it could be a different thread that actually throws the error. For example, thread 1 allocates a byte array that fills up all available heap space, then thread 2 tries to allocate a 1-byte array and throws an error.

[how-to-debug-java-outofmemory-exceptions](http://stackoverflow.com/questions/4512147/how-to-debug-java-outofmemory-exceptions)