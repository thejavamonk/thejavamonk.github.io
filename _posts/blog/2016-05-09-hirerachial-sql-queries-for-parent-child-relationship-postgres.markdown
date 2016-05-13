---
layout: post
title:  "Hirerachial sql queries in postgres"
date:   2016-05-09
categories: blog
tags: java
---

Postgres provides support for recursive SQL queries in the form of WITH and RECURSIVE queries.

WITH provides a way to write auxiliary statements for use in a larger query. These statements, which are often referred to as Common Table Expressions or CTEs, can be thought of as defining temporary tables that exist just for one query.

On its own, this might not seem like a big deal, but when combined with the optional RECURSIVE modifier, WITH queries can become quite powerful.

Using RECURSIVE along with WITH the query can access its own output. 

example:

{% highlight sql %}
WITH RECURSIVE t(n) AS (
     VALUES (1)
   UNION ALL
     SELECT n+1 FROM t WHERE n < 100
 )
 SELECT sum(n) FROM t;
 {% endhighlight %}

 References:
 1. [recursive-sql-in-activerecord](https://hashrocket.com/blog/posts/recursive-sql-in-activerecord)
 2. [PostgreSQL documentation](http://www.postgresql.org/docs/9.1/static/queries-with.html)