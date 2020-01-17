---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

You can also find my articles on <u><a href="https://scholar.google.com/citations?user={{site.author.googlescholar}}">my Google Scholar profile</a>.</u>

{% include base_path %}

<style>
td, th, tr, table {
  padding: 0.5em;
  border: 1px solid #ccc;
  border: 1px;
}
</style>

<table style="width:100%">
  {% for post in site.publications reversed %}
  <tr>
    <th style="width:40%">{{ post.excerpt | markdownify }}</th>
    <td>
      <h2 class="archive__item-title" itemprop="headline"> <a href="{{ base_path }}{{ post.url }}" rel="permalink">{{ post.title }}</a> </h2>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
      <p>Recommended citation: <br>
      {{ post.citation }} </p>
    </td>
  </tr>
  {% endfor %}
</table>

