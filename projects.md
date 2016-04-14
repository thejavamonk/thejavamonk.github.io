---
layout: default
title: all projects
permalink: /projects/
---

<div class="site-section site-section-last">
	<div class="wrapper"> 
		<header class="post-header">
			<h1>{{ page.title }}</h1>
		</header>
			<ul class="project-list">
	          {% for project in site.categories['project'] reversed %} 
	          {% include project.html %}
	          {% endfor %}
	        </ul>
    </div>
</div>
