<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  {% include head.md %}
  <body>
    {% include mainbar.md %}
    {% include beginpage.md %}
    <div class="main-content">
      {{ content }}
    </div>
    {% include footer.md %}
    {% if site.google_analytics %}
      <script type="text/javascript">
        (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
        (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
        m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
        })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

        ga('create', '{{ site.google_analytics }}', 'auto');
        ga('send', 'pageview');
      </script>
    {% endif %}
    
    <script type="text/javascript">
      window._idl = {};
      _idl.variant = "modal";
      (function() {
          var idl = document.createElement('script');
          idl.async = true;
          idl.src = 'https://members.internetdefenseleague.org/include/?url=' + (_idl.url || '') + '&campaign=' + (_idl.campaign || '') + '&variant=' + (_idl.variant || 'modal');
          document.getElementsByTagName('body')[0].appendChild(idl);
      })();
    </script>
  </body>
</html>
