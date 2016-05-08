---
layout: post
title:  "Unexpected error trying to gauge level of JDBC REF_CURSOR"
date:   2016-05-08
categories: blog
tags: java
---

The root cause seems to be the loading  of ALL META DATA, including comments beside sql columns and various other constructs. This feature is true by default and needs to be explicitly set to false by adding the below config in hibernate.cfg.xml or persistance.xml.

{% highlight xml %}
<property name="hibernate.jdbc.use_get_generated_keys" value="true" />
<prop key="hibernate.temp.use_jdbc_metadata_defaults">false</prop>
{% endhighlight %}

references:

[hibernate-slow-to-acquire-postgres-connection](http://stackoverflow.com/questions/10075081/hibernate-slow-to-acquire-postgres-connection)
