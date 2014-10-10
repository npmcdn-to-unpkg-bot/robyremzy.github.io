---
layout: page
title: Purpose in Progress
tagline: 
---
{% include JB/setup %}

## Posts

Here's a "posts list".

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## To-Do

-  About Page or a relevant index
-  Personal Themes
