---
layout: default
title: Home
---
# Welcome to my blog! 

I am planning on writing a lot of gooey thoughts. It's mostly to get out my ideas and improve my thinking.

{% for post in site.posts %}
<article>
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>

</article>
{% endfor %}
