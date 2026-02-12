---
layout: page
title: List of Articles
permalink: /articles/page2/
---

<div class="site-section site-section-last">
	{% assign blog_posts = site.posts | where: "categories", "blog" %}
	{% assign posts_per_page = 5 %}
	{% assign current_page = 2 %}
	
	{% assign offset = current_page | minus: 1 | times: posts_per_page %}
	{% assign total_posts = blog_posts | size %}
	{% assign total_pages = total_posts | divided_by: posts_per_page %}
	{% assign remainder = total_posts | modulo: posts_per_page %}
	{% if remainder != 0 %}
		{% assign total_pages = total_pages | plus: 1 %}
	{% endif %}
	
	<ul class="post-list">
		{% for post in blog_posts limit: posts_per_page offset: offset %}
		<li class="post">
			{% include post.html %}
		</li>
		{% endfor %}
	</ul>
	
	<!-- Pagination -->
	<div class="pagination">
		{% if current_page > 1 %}
			{% if current_page == 2 %}
				<a href="/articles/" class="pagination-link">&larr; Previous</a>
			{% else %}
				<a href="/articles/page{{ current_page | minus: 1 }}/" class="pagination-link">&larr; Previous</a>
			{% endif %}
		{% else %}
			<span class="pagination-link-disabled">&larr; Previous</span>
		{% endif %}
		
		<span class="pagination-info">Page {{ current_page }} of {{ total_pages }}</span>
		
		{% if current_page < total_pages %}
			<a href="/articles/page{{ current_page | plus: 1 }}/" class="pagination-link">Next &rarr;</a>
		{% else %}
			<span class="pagination-link-disabled">Next &rarr;</span>
		{% endif %}
	</div>
</div>
