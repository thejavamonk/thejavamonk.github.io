---
layout: post
title:  "Git cheat sheet"
date:   2016-05-09
categories: blog
tags: java
---

**how to pull from remote git repository and override the changes in my local repository**

{% highlight unix %}
git fetch origin
git reset --hard origin/{your branch}
{% endhighlight %}

**Unstage all the changes**

You can unstage files from the index using
{% highlight unix %}
git reset HEAD -- path/to/file
{% endhighlight %}
Just like git add, you can unstage files recursively by directory and so forth, so to unstage everything at once, run this from the root directory of your repository:
{% highlight unix %}
git reset HEAD -- .
{% endhighlight %}

**Merging changes and stashing**

Stashing acts as a stack, where you can push changes, and you pop them in reverse order.
To stash type:
{% highlight unix %}
git stash
{% endhighlight %}
Do the merge, and then pull the stash:
{% highlight unix %}
git stash pop
{% endhighlight %}

**error: You have not concluded your merge (MERGE_HEAD exists).**

Check status (git status) of your repository. Every unmerged file (after you resolve conficts by yourself) should be added (git add), and if there is no unmerged file you should git commit