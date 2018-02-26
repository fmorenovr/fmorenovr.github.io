<div id="mySidenav" class="sidenav">
  <a href="javascript:void(0)" class="closebtn" onclick="closeNav()">&times;</a>
  <strong><a href="/">Home</a></strong>
  <strong><a href="/about">About</a></strong>
  <strong><a href="/blog">Blog</a></strong>
</div>
<script>
function openNav() {
  document.getElementById("mySidenav").style.width = "160px";
  document.body.style.backgroundColor = "rgba(0,0,0,0.4)";
}

function closeNav() {
  document.getElementById("mySidenav").style.width = "0";
  document.body.style.backgroundColor = "white";
}
</script>
