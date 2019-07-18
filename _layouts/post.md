---
layout: default
---
<article itemscope itemtype="http://schema.org/BlogPosting">
  <!--contenido de layout: post de la carpeta _posts-->
  <div align="center"><p class="meta">This post was published at <strong>{{ page.date | date_to_string }}</strong></p></div>
  <div class="post">
    {{ content }}
  </div>

  {% include disqus_comments.md %}
</article>
