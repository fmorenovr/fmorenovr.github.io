<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  {% include head.md %}
  <body>
    {% include mainbar.md %}
    {% include beginpage.md %}
    <div class="main-content">
      {{ content }}
    </div>
    {% include acknowledgments.md %}
    {% include footer.md %}
  </body>
</html>
