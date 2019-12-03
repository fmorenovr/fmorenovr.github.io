---
layout: archive
permalink: /blog/
title: "Blog posts"
author_profile: true
redirect_from:
  - /blog-posts/
---

{% include base_path %}

## What is Computer Science?

Computer science is a discipline that spans theory and practice based on mathematics and physics. Computer scientists must be experienced in modeling and analyzing problems. With Computer Science, you can create anything and do anything :D.

{% capture written_year %}'None'{% endcapture %}
{% for post in site.posts %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% if year != written_year %}
    {% capture written_year %}{{ year }}{% endcapture %}
  {% endif %}
  {% include archive-single.html %}
{% endfor %}
