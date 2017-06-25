<header class="site-header" role="banner">
  <div class="wrapper">
    <a class="site-title" href="/">{{ site.title }}</a>
    <div class="site-nav" id="myTopnav">
      {% for page in site.pages %}
        {% if page.title and page.title != "Home" and page.title and page.title != "CV" and page.dir != "/pages/" %}
          <a class="page-link" href="{{ page.url | prepend: site.baseurl }}">{{ page.title }}</a>
        {% endif %}
      {% endfor %}
    </div>
  </div>
  <script>
    function myFunction() {
      var x = document.getElementById("myTopnav");
      if (x.className === "site-nav") {
        x.className += "trigger";
      } else {
        x.className = "site-nav";
      }
    }
</script>
</header>
