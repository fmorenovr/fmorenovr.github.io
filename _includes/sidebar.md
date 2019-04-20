<div id="mySidebar" class="sidebar">
  {% assign entry = site.data.navigation.sidebar %}
  {% assign sublinks = entry.sublinks %}
  {% if sublinks %}
    {% for sublink in sublinks %}
      <a href="{{ site.baseurl }}{{ sublink.url }}" class="{{sublink.class}}"><strong>{{ sublink.title }}</strong></a>
    {% endfor %}
  {% endif %}
  <!--<a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>-->
</div>
<script>
  function interactNav(){
    if (!visible) {
      openNav()
    } else {
      closeNav()
    }
  }

  function openNav() {
    document.getElementById("mySidebar").style.width = "130px";
    document.body.style.backgroundColor = "rgba(0,0,0,0.3)";
    visible = true
  }

  function closeNav() {
    document.getElementById("mySidebar").style.width = "0";
    document.body.style.backgroundColor = "white";
    visible = false
  }

  document.onclick= function(event) {
    // Compensate for IE<9's non-standard event model
    //
    if (event===undefined) event= window.event;
    var target= 'target' in event? event.target : event.srcElement;

    console.log('clicked on '+target.tagName);
    if(visible) console.log(visible)//closeNav()
  };
</script>
