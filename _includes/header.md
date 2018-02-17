<header class="site-header" role="banner">
  <div class="wrapper">
    <a class="site-title" href="/">{{ site.title }}</a>
    <div class="site-nav" id="myTopnav">
      {% for page in site.pages %}
        {% if page.dir != "/" and page.dir != "/cv/" and page.dir != "/pages/" and page.dir != "/docs/" and page.title != "Not Found" and page.dir != "/files/" and page.dir != "/privacyPolicy/" %}
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
