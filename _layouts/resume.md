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
    <script>
      (function () {
        var stored = localStorage.getItem("theme");
        var theme = stored || (window.matchMedia("(prefers-color-scheme: dark)").matches ? "dark" : "light");
        document.documentElement.setAttribute("data-theme", theme);
      })();
    </script>

{% seo %}
    <script src="https://kit.fontawesome.com/e679b7db17.js" crossorigin="anonymous"></script>
    <link rel="stylesheet" href="{{ "/assets/css/style.css?v=" | append: site.github.build_revision | relative_url }}">
    <!--[if lt IE 9]>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv.min.js"></script>
    <![endif]-->
  </head>
  <body>
    <div class="wrapper">
      <section>

      {{ content }}

      </section>
    </div>
    <script src="{{ "/assets/js/scale.fix.js" | relative_url }}"></script>
    <script>
      (function () {
        var root = document.documentElement;
        var btn = document.getElementById("theme-toggle");
        var icon = btn.querySelector("i");
        function sync() {
          icon.className = root.getAttribute("data-theme") === "dark" ? "fas fa-sun" : "fas fa-moon";
        }
        sync();
        btn.addEventListener("click", function () {
          var next = root.getAttribute("data-theme") === "dark" ? "light" : "dark";
          root.setAttribute("data-theme", next);
          localStorage.setItem("theme", next);
          sync();
        });
      })();
    </script>
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
