---
layout: default
---

# Latest News

<ul>
  {% for post in site.posts limit:10 %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>

<div style="text-align:center">
<a href="allnews.html">All the news</a>
</div>
