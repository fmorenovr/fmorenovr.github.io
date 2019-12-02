---
layout: compress
---

{% include base_path %}

<!doctype html>
<html lang="{{ site.locale | slice: 0,2 }}" class="no-js">
  <head>
    {% include head.md %}
    {% include head/custom.md %}
  </head>

  <body>

    {% include browser-upgrade.html %}
    {% include masthead.html %}

    {{ content }}


    {% include scripts.html %}

  </body>
</html>
