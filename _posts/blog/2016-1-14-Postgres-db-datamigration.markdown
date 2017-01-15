---
layout: post
title:  "postgres database migration"
date:   2017-01-14
categories: blog
tags: java
---

Steps to perform a postgres db data migration

1. Create the backup:

{% highlight psql %}
pg_dump mydb > db.sql
{% endhighlight %}

Copy db.sql to the new server (specific command depends on OS). Go to the new server

{% highlight psql %}
createdb mydb -E UTF8 (you don't have to specify UTF8 encoding, but I always do)
{% endhighlight %}

Then:

{% highlight psql %}
psql -d mydb -f db.sql
{% endhighlight %}

References:
http://dba.stackexchange.com/questions/23053/copy-postgresql-data-from-one-pc-to-another
https://www.howtoforge.com/how-to-easily-migrate-a-postgresql-server-with-minimal-downtime
https://www.digitalocean.com/community/tutorials/how-to-back-up-restore-and-migrate-postgresql-databases-with-barman-on-centos-7
http://engineering.tilt.com/7-postgresql-data-migration-hacks/