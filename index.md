---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
title: Home
---
# Welcome to my website!!

>Nice to meet you !!  
>You can find me on many websites with the alias Jenazad or Jenazads.  
>Here i will tell about me, my projects, my repositories and maybe some tutorials.

So, let's go!.  
Here is an example of my `index.md` listing my posts.

{% highlight html %}
<div class="home">
  <h1 class="page-heading">Welcome !!</h1>
  <p>This an example of HTML embebbed on markdown.<br>
  <ul class="post-list">
    <li>
      <span class="post-meta">Mar 20, 2017</span>
      <h2>
        <a class="post-link" href="link_to_Virt_Manager">Using Virt-Manager VM</a>
      </h2>
    </li>
  </ul>
  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>
</div>
{% endhighlight %}
