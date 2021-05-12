<!--
  <ul>{% for post in site.publications reversed %}
    <li>
      <h3 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a></h3>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
    </li>
  {% endfor %}</ul>

Oral presentations and Poster sessions
======
### Posters  
  <ul>{% for post in site.posters reversed %}
    <li>
      <h3 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a></h3>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
    </li>
  {% endfor %}</ul>
-->