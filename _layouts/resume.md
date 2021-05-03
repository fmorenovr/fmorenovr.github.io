---
layout: compress
---

{% include base_path %}

{% if page.author and site.data.authors[page.author] %}
  {% assign author = site.data.authors[page.author] %}{% else %}{% assign author = site.author %}
{% endif %}

<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  <head>
    <meta charset="UTF-8">
    <link rel="shortcut icon" href="/assets/images/favicon.ico?v=M44lzPylqQ">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">

{% seo %}
    <script src="https://kit.fontawesome.com/e679b7db17.js" crossorigin="anonymous"></script>
    <link rel="stylesheet" href="{{ "/assets/css/style.css?v=" | append: site.github.build_revision | relative_url }}">
    <!--[if lt IE 9]>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <div class="wrapper">
      <header style="text-align: center;">
        <h1><a href="{{ "/" | absolute_url }}">Felipe A. Moreno</a></h1>
        
        {% if author.avatar %}
          <img src="/assets/me/me_2017.png" alt="{{ author.name }}" width="240" />
        {% endif %}

        <br /><p style="margin: 1em 0">Artificial Intelligence Engineer at <a href="https://portal.fgv.br/">Fundação Getúlio Vargas (FGV)</a>.</p>

        <div style="text-align: left;">
          <!--
          <p class="view"><a href="/projects.html"><i class='fa fa-cog'></i> &nbsp; Projects</a></p>
          <p class="view"><a href="/publications.html"><i class='far fa-file-alt'></i> &nbsp; Publications</a></p>
          -->
          <p class="view"><a href="https://www.kaggle.com/fmorenovr" target="_blank"><i class='fab fa-kaggle'></i> &nbsp; Kaggle</a></p>
          <p class="view"><a href="https://www.linkedin.com/in/{{author.linkedin}}" target="_blank"><i class='fab fa-linkedin'></i> &nbsp; LinkedIn</a></p>
          <p class="view"><a href="https://github.com/{{ author.github }}"><i class='fab fa-github'></i> &nbsp; GitHub</a></p>
          <p class="view"><a href="https://scholar.google.com/citations?user={{ author.googlescholar }}"><i class="fas fa-fw fa-graduation-cap"></i> &nbsp; Google Scholar</a>
        </div>
      </header>
      <section>

      {{ content }}

      </section>
      <footer>
        {% if site.github.is_project_page %}
        <p>This project is maintained by <a href="{{ site.github.owner_url }}">{{ site.github.owner_name }}</a></p>
        {% endif %}
      </footer>
    </div>
    <script src="{{ "/assets/js/scale.fix.js" | relative_url }}"></script>
    {% if site.google_analytics %}
    <!-- Global site tag (gtag.js) - Google Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id={{ site.google_analytics }}"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());
      gtag('config', '{{ site.google_analytics }}');
    </script>
    {% endif %}
  </body>
</html>