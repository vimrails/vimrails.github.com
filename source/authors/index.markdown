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
      I'm a ruby on rails developer, although I do other stuff, too.

      I made this blog using [octopress](http://octopress.org).

      Ask me about [Lua](http://www.lua.org).

---

{% for author in page.authors do %}
<h2 id="{{author.id}}"><a href="{{ author.url }}">{{ author.name }} <small>({{ author.id }})</small></a></h2>

{{ author.bio }}

{% endfor %}
