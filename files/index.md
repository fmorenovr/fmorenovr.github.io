---
layout: default
permalink: /files/
---
<h1> Files </h1>
<p> List of files on my website for your download </p>
{% for file in site.static_files %}
  {% if file.extname == ".zip" or file.extname == ".rar" or file.extname == ".7z" %}
   * [{{ file.name}}]({{ site.baseurl }}{{ file.path }})
  {% endif %}
{% endfor %}

