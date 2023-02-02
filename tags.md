---
layout: page
title: Tags
---

<h1>Posts sorted by tags</h1>
<hr />
<div class="tags-expo">
	<div class="tags-expo-section">
		{% for tag in site.tags %}
			<h2 id="{{ tag[0] | slugify }}">
				{{ tag[0] }}
			</h2>
			<ul class="tags-expo-posts">
				{% for post in tag[1] %}
					<li>
						<a class="item-title" href="{{ site.baseurl }}{{ post.url }}">
							<span class="title">{{ post.title }}</span>
							<time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">
								{{ post.date | date_to_string }}
							</time>
						</a>
					</li>
				{% endfor %}
			</ul>
		{% endfor %}
	</div>
</div>
