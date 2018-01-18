---
layout: post
title:  "API design Java"
date:   2016-12-26
categories: blog
tags: java
---


<h4 style="text-align: left;"> 1. Do not Return Null to Indicate the Absence of a Value </h4>
 

Make sure a method that can return a no-value returns an Optional instead of null.
<br>
Java 8’s escape analysis will optimize away most Optional objects anyway. Avoid using Optionals in parameters and fields.

{% highlight java %}
public Optional<String> getComment() {
    return Optional.ofNullable(comment);
}
{% endhighlight %}

<h4 style="text-align: left;"> 2. Do not Use Arrays to Pass Values to and From the API </h4>



