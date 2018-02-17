---
layout: default
permalink: privacyPolitics/
---
<h1>Privacy politics pages</h1>
<ul>
  {% for page in site.pages %}
    {% if page.layout == "privacyPolitics" and page.dir == "/privacyPolitics/" %}
    <li>
        <a href="{{ page.url | prepend: site.baseurl }}">{{ page.subtitle | escape }}</a>
        <blockquote> {{page.description}}</blockquote>
    </li>
    {% endif %}
  {% endfor %}
</ul>
