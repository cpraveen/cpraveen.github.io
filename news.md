---
layout: default
title: News
---
<h1>Latest News</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.date | date_to_string }}: {{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
