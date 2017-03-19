---
# You don't need to edit this file, it's empty on purpose.
# Edit theme's home layout instead if you wanna make some changes
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
layout: default
title: Home
---
# Welcome to my website!!

>Nice to meet you !! You can find me on many websites with the alias Jenazad.

Here i will tell about me, my projects, my repositories and maybe some tutorials.

So, let's go!.

{% highlight html %}
<div class="home">
  <h1 class="page-heading">Welcome !!</h1>
  <p>Welcome to my website !!.<br>
  Here i will tell about me, my projects, my repositories and maybe some tutorials.<br>
  So, let's go!.</p>
  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title | escape }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>
  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>
</div>
{% endhighlight %}
