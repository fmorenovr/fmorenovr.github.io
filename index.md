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
  <p>Welcome to my website !!.<br>
  Here i will tell about me, my projects, my repositories and maybe some tutorials.<br>
  So, let's go!.</p>
  <ul class="post-list">
    <li>
        <span class="post-meta">Mar 20, 2017</span>
        <h2>
          <a class="post-link" href="/blog/2017/03/20/virtual-machines/Using-Virt-Manager">Using Virt-Manager VM</a>
        </h2>
      </li>
    
      <li>
        <span class="post-meta">Mar 15, 2017</span>
        <h2>
          <a class="post-link" href="/blog/2017/03/15/markup-language/Create-own-gedit-Theme">Creating my own gedit theme</a>
        </h2>
      </li>
    
      <li>
        <span class="post-meta">Mar 2, 2017</span>
        <h2>
          <a class="post-link" href="/blog/2017/03/02/operating-systems/Ubuntu-Desktop-environment">Playing with Ubuntu desktop environments</a>
        </h2>
      </li>
    
      <li>
        <span class="post-meta">Dec 19, 2016</span>
        <h2>
          <a class="post-link" href="/blog/2016/12/19/virtual-machines/Using-qemu-VM">Using Qemu VM hardware emulator</a>
        </h2>
      </li>
  </ul>
  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>
</div>
{% endhighlight %}
