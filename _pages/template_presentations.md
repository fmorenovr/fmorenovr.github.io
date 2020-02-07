---
layout: archive
title: "Presentations"
permalink: /presentations/
author_profile: true
---

{% include base_path %}

<style>
td, th, tr, table {
  padding: 0.5em;
  border: 1px solid #ccc;
  border: 1px;
}
</style>

<table style="width:100%">
  {% for post in site.presentations reversed %}
  <tr>
    <th style="width:40%; height:60%">{{ post.excerpt | markdownify }}</th>
    <td>
      <h2 class="archive__item-title" itemprop="headline"> <a href="{{ base_path }}{{ post.url }}" rel="permalink">{{ post.title }}</a> </h2>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
      <p>Abstract: <br>
      <i> {{ post.abstract }} </i></p>
      {% if post.paper and post.code %}
        <p> <a href="{{post.paper}}">Paper </a>, <a href="{{post.code}}"> Code</a> </p>
      {% elsif post.paper %}
        <p> <a href="{{post.paper}}">Paper </a> </p>
      {% elsif post.code %}
        <p> <a href="{{post.code}}">Code </a></p>
      {% endif %}
    </td>
  </tr>
  {% endfor %}
</table>

