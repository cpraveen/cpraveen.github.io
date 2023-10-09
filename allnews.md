---
layout: default
---

# News

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ page.date | date_to_string }}: {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
