<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  <head>
    <meta charset="UTF-8">
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
        <h1><a href="{{ "/" | absolute_url }}">{{ site.title | default: site.github.repository_name }}</a></h1>
        
        {% if site.logo %}
          <img src="{{site.logo | relative_url}}" alt="Logo" width="240" />
        {% endif %}

        <br /><p style="margin: 1em 0">{{ site.description | default: site.github.project_tagline }}</p>

        <div style="text-align: left;">
          <p class="view"><a href="/projects.html"><i class='fa fa-cog'></i> &nbsp; Projects</a></p>
          <p class="view"><a href="/publications.html"><i class='far fa-file-alt'></i> &nbsp; Publications</a></p>
          <p class="view"><a href="https://www.kaggle.com/murilocamargos" target="_blank"><i class='fab fa-kaggle'></i> &nbsp; Kaggle</a></p>
          <p class="view"><a href="https://www.linkedin.com/in/murilocamargos/" target="_blank"><i class='fab fa-linkedin'></i> &nbsp; LinkedIn</a></p>
          <p class="view"><a href="{{ site.github.owner_url }}"><i class='fab fa-github'></i> &nbsp; GitHub</a></p>
        </div>
      </header>
      <section>

      {{ content }}

      </section>
      <footer>
        {% if site.github.is_project_page %}
        <p>This project is maintained by <a href="{{ site.github.owner_url }}">{{ site.github.owner_name }}</a></p>
        {% endif %}
        <p><small>Hosted on GitHub Pages &mdash; Theme by <a href="https://github.com/orderedlist">orderedlist</a></small></p>
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