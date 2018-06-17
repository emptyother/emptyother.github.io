---
title: Blog
---

Posts: 
{% for post in site.posts %}
* [{{ post.title }}]({{ post.url }})
{% endfor %}

{% for post in site.posts %}

## [{{ post.title }}]({{ post.url }})

{{ post.excerpt }}

{% endfor %}

Categories:
{% for post in site.categories[page.category] %}
    * [{{ post.title }}]({{ post.url | absolute_url }})
{% endfor %}
