---
layout: page
title:  Blog
permalink: /blog/
---
<h1>My posts</h1>
<ul>
  {% for post in site.posts %}
    <li>
      <p>{{ post.date | date: "%b %-d, %Y" }}</p>
      <h2>
        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title | escape }}</a>
      </h2>
    </li>
  {% endfor %}
</ul>
