---
layout: page
title: Blog
---

<div class="blog">
	{%- if site.posts.size > 0 -%}
	<ul class="post-list">
		{%- for post in site.posts -%}
			<li>
				<h2>
					<a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
				</h2>
				<div class="post-meta">
					<span>Published</span>
					<div class="post-categories">
						<span>in</span>
						{% if post %}
							{% assign categories = post.categories %}
						{% else %}
							{% assign categories = page.categories %}
						{% endif %}
						{% for category in categories %}
							<a href="{{ site.baseurl }}/categories/#{{ category | slugize }}">{{ category }}</a>
							{% unless forloop.last %}&nbsp;{% endunless %}
						{% endfor %}
					</div>
					{%- if post.date -%}
						<span>
							<span>at</span>
							<time class="dt-published" datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished" >
								{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
								{{ post.date | date: date_format }}
							</time>
						</span>
					{%- endif -%}
					{%- if post.modified -%}
						<span>
							<span>(modified </span>
							<time class="dt-published" datetime="{{ post.modified | date_to_xmlschema }}" itemprop="datePublished" >
								{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
								{{ post.modified | date: date_format }}
							</time>
							<span>)</span>
						</span>
					{%- endif -%}
				</div>
				{%- if site.show_excerpts -%}
					{{ post.excerpt }}
					<p><a href="{{ post.url | relative_url }}">Read more...</a></p>
				{%- endif -%}
				{% if post.tags.size > 0 %}
					<div class="tag-list post-meta">
						<span class="tag-label">Tags:</span>
						{% for tag in post.tags %}
							{% capture tag_name %}{{ tag }}{% endcapture %}
							<a href="{{site.baseurl}}/tags/#{{tag_name}}" class="tag-link">{{ tag_name }}</a >{% unless forloop.last %},{% endunless %}
						{% endfor %}
					</div>
				{% endif %}
			</li>
		{%- endfor -%}
	</ul>
	<p class="rss-subscribe">
		<a href="{{ '/feed.xml' | relative_url }}">RSS</a>
	</p>
	{%- endif -%}
</div>
