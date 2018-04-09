<!-- esto es para el sidebar
<div>
<span style="padding:20px; float:left; font-size:200%;cursor:pointer; color: white;" onclick="openNav()">&#9776;</span>
</div>
-->
{% if page.imageBackground %}
<div class="page-header" style="background-image: url({{ page.imageBackground }}); background-repeat: no-repeat; color: #ff456f;">
{% else %}
<div class="page-header">
{% endif %}
  <h1 class="project-name">{{ page.title  }}</h1>
  <h2 class="project-tagline">
    {% if page.description %}
      {{ page.description }}
    {% else %}
      {% if page.subtitle %}
        {{ page.subtitle }}
      {% else %}
        {{ site.description }}
      {% endif %}
    {% endif %}
  </h2>
</div>
