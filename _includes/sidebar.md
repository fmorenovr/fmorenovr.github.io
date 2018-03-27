<div id="mySidebar" class="sidebar">
  <!--<a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>-->
  <a href="/" align="center"><strong>icon</strong></a>
  <a href="/about"><strong>About</strong></a>
  <a href="/blog"><strong>Blog</strong></a>
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
</script>
