---
layout: single
---
<article itemscope itemtype="http://schema.org/BlogPosting">
  <!--contenido de layout: post de la carpeta _posts-->
  <div class="post">
    {{ content }}
  </div>
  {% include disqus_comments.md %}
</article>
