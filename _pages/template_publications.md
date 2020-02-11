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
    <th style="width:40%; height:60%">{{ post.excerpt | markdownify }}</th>
    <td>
      <h2 class="archive__item-title" itemprop="headline"> <a href="{{ post.event }}" rel="permalink">{{ post.title }}</a> </h2>
      <p style="font-size:12px">Published in <i>{{ post.venue }}</i>, {{ post.date | default: "1900-01-01" | date: "%Y" }} </p>
      <p>Abstract: <br>
      <i> {{ post.abstract }} </i></p>
      <p>
      {% if post.paper %}
        <a href="{{post.paper}}"><img src="/assets/webpage/pdf_img.png" alt="Paper" style="width:28px;height:28px;border:0;"></a>
      {% endif %}
        <a class=""> <img src="/assets/webpage/bib_img.png" alt="Bib" style="width:28px;height:28px;border:0;"></a>
      {% if post.code %}
        <a href="{{post.code}}"> <img src="/assets/webpage/supplemental_img.png" alt="Supplemental" style="width:28px;height:28px;border:0;"></a>
      {% endif %}
      </p>
    </td>
  </tr>
  {% endfor %}
</table>

<script>
$(window).load(function () {
    $(".trigger_popup_fricc").click(function(){
       $('.hover_bkgr_fricc').show();
    });
    $('.hover_bkgr_fricc').click(function(){
        $('.hover_bkgr_fricc').hide();
    });
    $('.popupCloseButton').click(function(){
        $('.hover_bkgr_fricc').hide();
    });
});
</script>
