---
layout: page
title: Writing Archive
permalink: /archive/
---

<p>
  Technical writing from earlier in my engineering career.
</p>

<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    — {{ post.date | date: "%Y" }}
  </li>
{% endfor %}
</ul>