---
layout: page
title: "authors"
comments: true
sharing: true
footer: true

authors:
  - id: kikito
    name: Enrique García
    url: http://github.com/kikito
    twitter: otikik
    bio: |
      I like all good things.

      Ask me about Lua.

---

<ul>
{% for author in page.authors do %}
  <li><a href="{{ author.url }}">{{ author.name }}</a></li>
{% endfor %}
</ul>
