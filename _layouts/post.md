---
layout: default
---
<!--contenido de layout: post de la carpeta _posts-->
<h1>{{ page.title }}</h1>
<p class="meta">This post was published at <strong>{{ page.date | date_to_string }}</strong></p>
<div class="post">
  {{ content }}
</div>
