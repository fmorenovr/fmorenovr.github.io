---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}

  <p class="archive__item-excerpt" itemprop="description">{{ post.excerpt | markdownify }}</p>  
  <h2 class="archive__item-title" itemprop="headline">
    <a href="{{ base_path }}{{ post.url }}" rel="permalink">{{ title }}</a>
  </h2>
  <p>Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
  <p>Recommended citation: {{ post.citation }} </p>
{% endfor %}
