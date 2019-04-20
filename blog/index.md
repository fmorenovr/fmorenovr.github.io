---
layout: page
title:  Blog
permalink: /blog/
description: "This is my personal blog, here I write my posts about some tutorials"
---
<div align="center"><h1>Click on your interest topic</h1></div>
<ul>
  {% for post in site.posts %}
    <li>
      <p>{{ post.date | date: "%b %-d, %Y" }}</p>
      <h2>
        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title | escape }}</a>
      </h2>
      <blockquote> {{post.subtitle}}</blockquote>
    </li>
  {% endfor %}
</ul>
