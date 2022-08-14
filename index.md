---
layout: default
title: Home
---

> Hey there, I'm Sam Kalish. This is my blog. I think of it as a good medium to articulate issues I've had and showcase projects I've worked on.
> I'm a programmer at [Gamefam](https://gamefam.com/). I developed [SimpleAdmin](https://github.com/crywink/SimpleAdmin), SimpleAnticheat, and some other cool stuff.

{% for post in site.posts limit:5 %}
### {{ post.date | date_to_long_string }} <a href="{{ post.url }}">{{ post.title }}</a>
{{ post.excerpt }}
{% endfor %}

### [More...](/archives/)
