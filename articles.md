---
layout: page
title: List of Articles
permalink: /articles/
---

<div class="site-section site-section-last">
	<ul class="post-list">
          {% for post in site.categories['blog'] %}
          <li class="post">
            {% include post.html %}
          </li>
          {% endfor %}
    </ul>
</div>