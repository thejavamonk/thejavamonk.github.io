---
layout: post
title:  "Steps to install vnc server on rhel"
date:   2016-02-24 17:59:44 +0530
categories: blog
tags: linux
---

#1. Execute the following commands

{% highlight unix %}
    yum groupinstall "X Window System" "Desktop"
    yum -y install tigervnc-server xorg-x11-fonts-Type1
    yum install xterm 
{% endhighlight %}
      

2. Create a vncuser

{% highlight unix %}
    adduser <username>
    passwd <users password>
{% endhighlight %}

3. Switch to user account and execute vncpasswd that will create a .vnc directory.

{% highlight unix %}
    su <username>
    vncpasswd
{% endhighlight %}

4. Edit the vncserver configuration

{% highlight unix %}
    vi /etc/sysconfig/vncservers 
    VNCSERVERS="2:<username>"
    VNCSERVERARGS[2]="-geometry 1366x768"
{% endhighlight %}

5. Start vncserver by executing

{% highlight unix %}
    service vncserver start
{% endhighlight %}