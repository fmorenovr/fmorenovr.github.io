---
layout: archive
title: "Posters"
permalink: /posters/
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
  {% for post in site.posters reversed %}
  <tr>
    <th style="width:40%; height:60%">{{ post.excerpt | markdownify }}</th>
    <td>
      <!--<h2 class="archive__item-title" itemprop="headline"> <a href="{{ base_path }}{{ post.url }}" rel="permalink">{{ post.title }}</a> </h2>-->
      <h2 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a> </h2>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
      <p>Abstract: <br>
      <i> {{ post.abstract }} </i></p>
      <p>
      {% if post.paper %}
        <a href="{{post.paper}}"><img src="/assets/webpage/pdf_img.png" alt="Paper" style="width:28px;height:28px;border:0;"></a>
      {% endif %}
        <a href=""> <img src="/assets/webpage/bib_img.png" alt="Bib" style="width:28px;height:28px;border:0;"></a>
      {% if post.code %}
        <a href="{{post.code}}"> <img src="/assets/webpage/supplemental_img.png" alt="Supplemental" style="width:28px;height:28px;border:0;"></a>
      {% endif %}
      </p>
    </td>
  </tr>
  {% endfor %}
</table>

