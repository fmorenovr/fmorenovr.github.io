---
layout: default
permalink: pages/
---
<h1>My pages</h1>
<ul>
  {% for page in site.pages %}
    {% if page.layout == "page" and page.dir == "/pages/" %}
    <li>
        <a href="{{ page.url | prepend: site.baseurl }}">{{ page.subtitle | escape }}</a>
        <blockquote> {{page.description}}</blockquote>
    </li>
    {% endif %}
  {% endfor %}
</ul>
