<!-- esto es para el sidebar
<div>
<span style="padding:20px; float:left; font-size:200%;cursor:pointer; color: white;" onclick="openNav()">&#9776;</span>
</div>
-->
{% if page.imageBackground %}
<div class="page-header" style="background-image: linear-gradient(rgba(255,255,255,.5), rgba(0,0,0,.5)), url({{ page.imageBackground }}); color: #000;">
{% else %}
<div class="page-header" style="background-image: linear-gradient(120deg, #155799, #159957); color: #fff;">
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
