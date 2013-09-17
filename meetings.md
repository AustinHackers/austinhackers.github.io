---
layout: default
title: Meeting Calendar
categories: nav
showinnav: true
---

<div id="home">
  <h1>{{ page.title }}</h1>
  <ul class="posts">
    {% for post in site.posts %}
  
      {% unless post.next %}
        <h2>{{ post.date | date: '%Y' }}</h2>
      {% else %}
        {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
        {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
        {% if year != nyear %}
          <h2>{{ post.date | date: '%Y' }}</h2>
        {% endif %}
      {% endunless %}
  
      <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>
</div>
