---
layout: default
permalink: docs/
---
<h1>My docs pages</h1>
<ul>
  {% for page in site.pages %}
    {% if page.layout == "page" and page.dir == "/docs/" %}
    <li>
        <a href="{{ page.url | prepend: site.baseurl }}">{{ page.subtitle | escape }}</a>
        <blockquote> {{page.description}}</blockquote>
    </li>
    {% endif %}
  {% endfor %}
</ul>
