---
layout: page
title: Files
permalink: /files/
# si el link no coincide con el nombre de la carpeta (o simplemente le ponemos undefinedurl/, nos manda al parent).
# o si no existe el index.md en la carpeta, muestra el parent.
---
<p> List of files on my website for your download </p>
{% for file in site.static_files %}
  {% if file.extname == ".zip" or file.extname == ".rar" or file.extname == ".7z" %}
   * [{{ file.path | remove: "/files/" }}]({{ site.baseurl }}{{ file.path }})
  {% endif %}
{% endfor %}

