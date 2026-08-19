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
        {% if author.avatar %}
          <img src="/assets/me/me_2025.png" alt="{{ author.name }}" class="avatar" width="250"/>
        {% endif %}
        <div class="social-icons">
          <a href="https://www.linkedin.com/in/{{author.linkedin}}" target="_blank" title="LinkedIn"><i class='fab fa-linkedin'></i></a>
          <a href="https://www.twitter.com/in/{{author.twitter}}" target="_blank" title="Twitter"><i class='fab fa-twitter'></i></a>
          <a href="https://www.instagram.com/in/{{author.instagram}}" target="_blank" title="Instagram"><i class='fab fa-instagram'></i></a>
          <a href="https://github.com/{{ author.github }}" target="_blank" title="GitHub"><i class='fab fa-github'></i></a>
          <a href="https://scholar.google.com/citations?user={{ author.googlescholar }}" target="_blank" title="Google Scholar"><i class="fas fa-fw fa-graduation-cap"></i></a>
        </div>
      </header>
      <section>

      {{ content }}

      </section>
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
