<header class="site-header" role="banner">
  <div class="wrapper">
    <a class="site-title" href="/">{{ site.title }}</a>
    <nav class="site-nav">
      <div class="trigger">
        {% for page in site.pages %}
          {% if page.title and page.title != "Home" and page.dir != "/pages/" %}
            <a class="page-link" href="{{ page.url | prepend: site.baseurl }}">{{ page.title }}</a>
          {% endif %}
        {% endfor %}
      </div>
    </nav>
  </div>
</header>
