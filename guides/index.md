---
layout: default
title: Guide pages 
subtitle: Some basic configurations, is like a documentation page.
permalink: /guides/
---
<div align="center"><h1>My guide pages</h1></div>
<ul>
  {% for page in site.pages %}
    {% if page.layout == "page" and page.dir == "/guides/" %}
    <li>
        <a href="{{ page.url | prepend: site.baseurl }}">{{ page.subtitle | escape }}</a>
        <blockquote> {{page.description}}</blockquote>
    </li>
    {% endif %}
  {% endfor %}
</ul>
