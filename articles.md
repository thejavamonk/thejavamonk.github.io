---
layout: page
title: List of Articles
permalink: /articles/
pagination:
  enabled: true
  collection: posts
  category: blog
  per_page: 5
---

<div class="site-section site-section-last">
	<ul class="post-list">
		{% for post in paginator.posts %}
		<li class="post">
			{% include post.html %}
		</li>
		{% endfor %}
	</ul>
	
	<!-- Pagination -->
	{% if paginator.total_pages > 1 %}
	<div class="pagination">
		{% if paginator.previous_page %}
			<a href="{{ paginator.previous_page_path | prepend: site.baseurl }}" class="pagination-link">&larr; Previous</a>
		{% else %}
			<span class="pagination-link-disabled">&larr; Previous</span>
		{% endif %}
		
		<span class="pagination-info">Page {{ paginator.page }} of {{ paginator.total_pages }}</span>
		
		{% if paginator.next_page %}
			<a href="{{ paginator.next_page_path | prepend: site.baseurl }}" class="pagination-link">Next &rarr;</a>
		{% else %}
			<span class="pagination-link-disabled">Next &rarr;</span>
		{% endif %}
	</div>
	{% endif %}
</div>