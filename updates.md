---
layout: page
title: Updates
---

{% for post in site.posts %}
{% assign currentdate = post.date | date: "%Y" %}
{% if currentdate != date %}
<ul class="years">
    <li id="y{{currentdate}}">{{ currentdate }}</li>
</ul>
{% assign date = currentdate %}
{% endif %}
<ul class="posts">
    <li><a href="{{ post.url }}">{{ post.date | date: "%-d %b %Y" }} • {{ post.title }}</a></li>
</ul>
{% endfor %}