---
layout: post
title:  "postgres cheatsheet"
date:   2017-01-15
categories: blog
tags: postgres
---

<div>
		1. List tables in a PostgreSQL schema

		In all schemas:
		{% highlight psql %}
		=> \dt *.*
		{% endhighlight %}

		In a particular schema:
		{% highlight psql %}
		=> \dt public.*
		{% endhighlight %}
</div>

<div>
		2. Drop all tables in PostgreSQL

		If all of your tables are in a single schema, this approach could work (below code assumes that the name of your schema is public)

		{% highlight psql %}
		DROP SCHEMA public CASCADE;
		CREATE SCHEMA public;
		{% endhighlight %}

		If you are using PostgreSQL 9.3 or greater, you may also need to restore the default grants.

		{% highlight psql %}
		GRANT ALL ON SCHEMA public TO postgres;
		GRANT ALL ON SCHEMA public TO public;
		{% endhighlight %}
</div>
