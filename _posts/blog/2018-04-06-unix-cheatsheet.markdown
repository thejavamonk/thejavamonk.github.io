---
layout: post
title:  "Unix cheat"
date:   2016-12-26
categories: blog
tags: java
---

**recursively search for a value in all files present in a directory**

{% highlight unix %}
grep -rnw '/path/to/somewhere/' -e 'pattern'
{% endhighlight %}


    -r or -R is recursive,
    -n is line number, and
    -w stands for match the whole word.
    -l (lower-case L) can be added to just give the file name of matching files.

source: https://stackoverflow.com/questions/16956810/how-do-i-find-all-files-containing-specific-text-on-linux