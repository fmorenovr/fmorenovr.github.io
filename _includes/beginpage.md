<!-- esto es para el sidebar
<div>
<span style="padding:20px; float:left; font-size:200%;cursor:pointer; color: white;" onclick="openNav()">&#9776;</span>
</div>
-->
<div class="page-header">
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
