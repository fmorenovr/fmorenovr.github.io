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

document.onclick= function(event) {
  // Compensate for IE<9's non-standard event model
  //
  if (event===undefined) event= window.event;
  var target= 'target' in event? event.target : event.srcElement;

  console.log('clicked on '+target.tagName);
  if(visible) console.log(visible)//closeNav()
};

</script>
