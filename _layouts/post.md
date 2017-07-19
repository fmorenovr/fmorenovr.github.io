---
layout: default
permalink: /blog/:categories/:year/:month/:day/:title
---
<!--contenido de layout: post de la carpeta _posts-->
<h1>{{ page.title }}</h1>
<p class="meta">{{ page.date | date_to_string }}</p>
<div class="post">
  {{ content }}
</div>
