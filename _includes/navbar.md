<div id="myNavbar" class="navbar">
  {% assign entry = site.data.navigation.navbar %}
  {% assign sublinks = entry.sublinks %}
  {% if sublinks %}
    {% for sublink in sublinks %}
      <a href="{{ site.baseurl }}{{ sublink.url }}" class="{{sublink.class}}"><strong>{{ sublink.title }}</strong></a>
    {% endfor %}
  {% endif %}
  <a href="javascript:void(0);" style="font-size:15px;" class="icon" onclick="interactNav()">&#9776;</a>
</div>
<script>
  var visible = false
</script>
