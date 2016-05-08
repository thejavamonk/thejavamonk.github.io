---
layout: post
title:  "Unexpected error trying to gauge level of JDBC REF_CURSOR"
date:   2016-05-08
categories: blog
tags: java
---

The root cause seems to be the loading  of ALL META DATA, including comments beside sql columns and various other constructs. This feature is true by default and needs to be explicitly set to false by adding the below config in hibernate.cfg.xml or persistance.xml.

{% highlight xml %}
<prop key="hibernate.temp.use_jdbc_metadata_defaults">false</prop>
{% endhighlight %}

references:
