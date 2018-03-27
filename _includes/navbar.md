<div id="myNavbar" class="navbar">
  <a href="/" class="homeoption"><strong>Home</strong></a>
  <a href="/blog" class="otheroptions"><strong>Blog</strong></a>
  <a href="/about" class="otheroptions"><strong>About</strong></a>
  <a href="javascript:void(0);" style="font-size:15px;" class="icon" onclick="interactNav()">&#9776;</a>
</div>
<script>
var visible = false
function evalNav() {
  var x = document.getElementById("myNavbar");
  if (x.className === "navbar") {
    x.className += " responsive";
    console.log("set navbar responsive");
  } else {
    x.className = "navbar";
    console.log("set navbar");
  }
}
</script>

