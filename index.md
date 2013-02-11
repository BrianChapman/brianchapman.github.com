---
layout: page
title: Brian Chapman - Blog
tagline: RidgeTop Solutions
---
{% include JB/setup %}

{% for post in site.posts %}
<div>
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
  <p>{{ post.date | date_to_string }} - {{site.author.name}}</p>
  <p>{{ post.content | strip_html | truncatewords: 55 }}</p>
  <a href="{{ post.url }}">Read more ...</a>
</div>
{% endfor %}



