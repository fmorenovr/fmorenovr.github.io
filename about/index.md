---
layout: page
title: About
permalink: /about/
description: "Here you would find information about me :D "
---
<div align="center">
<p>
  You can find the source code at <a href="https://github.com/Jenazads">Jenazads</a>/<a href="https://github.com/Jenazads/Jenazads.github.io">JenazadsWebsite</a>. <br>
  I am a Computer Scientist graduated of the <a href="http://www.uni.edu.pe">National University of Engineering</a> Lima-Peru.<br><br>
  <img style="border-radius: 25px;border: 2px solid #73AD21;" src="/assets/me/me_huacachina.jpg">
  <br>
  <br>
  <h2>What is Computer Science?</h2>
  Computer science is a discipline that spans theory and practice based on mathematics and physics.
  <br>
  Computer scientists must be experienced at modeling and analyzing problems.
  <br>
  With computer Science you can create anything and ... do anything :D
</p>
</div>
<div align="center">
  <h2>Contact to me</h2>
  <ul class="contact-list">
    Email me: <br>
    {% if site.author.gmail %}
      <a href="mailto:{{ site.author.gmail }}">
        <span class="icon icon--email">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
              <path d="M7,9L5.268,7.484l-4.952,4.245C0.496,11.896,0.739,12,1.007,12h11.986 c0.267,0,0.509-0.104,0.688-0.271L8.732,7.484L7,9z M13.684,2.271C13.504,2.103,13.262,2,12.993,2H1.007C0.74,2,0.498,2.104,0.318,2.273L7,8 L13.684,2.271z"/>
            <polygon points="0,2.878 0,11.186 4.833,7.079"/>
            <polygon points="9.167,7.079 14,11.186 14,2.875"/>
          </svg>
        </span>
        <span class="email">Gmail</span>
      </a>&nbsp;
    {% endif %}
    <br>
  </ul>
</div>
<div align="center">
  <ul class="contact-list">
    Follow me: <br>
  </ul>
  <ul id="list-contact-menu">
    {% if site.twitch_username %}
      <a href="{{site.twitch_url}}{{site.twitch_username }}">
        <span class="icon icon--twitch">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
            <img src="/assets/images/socialnetwork/twitch_32.png"/>
          </svg>
        </span>
        <span class="username">{{ site.twitch_username }}</span>
      </a>
    {% endif %}
    {% if site.vimeo_username %}
      <a href="{{site.vimeo_url}}{{site.vimeo_username }}">
        <span class="icon icon--vimeo">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
            <img src="/assets/images/socialnetwork/vimeo_32.png"/>
          </svg>
        </span>
        <span class="username">{{ site.vimeo_username }}</span>
      </a>
    {% endif %}
    {% if site.github_username %}
      <a href="{{site.github_url}}{{site.github_username }}">
        <span class="icon icon--github">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
            <img src="/assets/images/socialnetwork/github_32.png"/>
          </svg>
        </span>
        <span class="username">{{ site.github_username }}</span>
      </a>
    {% endif %}
    {% if site.linkedin_username %}
      <a href="{{site.linkedin_url}}{{ site.linkedin_username }}">
        <span class="icon icon--linkedin">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
            <img src="/assets/images/socialnetwork/linkedin_32.png"/>
          </svg>
        </span>
        <span class="username">{{ site.linkedin_username }}</span>
      </a>
    {% endif %}
  </ul>
  <ul id="list-contact-menu">
    {% if site.twitter_username %}
      <a href="{{site.twitter_url}}{{ site.twitter_username }}">
        <span class="icon icon--twitter">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
            <img src="/assets/images/socialnetwork/twitter_32.png"/>
          </svg>
        </span>
        <span class="username">{{ site.twitter_username }}</span>
      </a>
    {% endif %}
    {% if site.facebook_username %}
      <a href="{{site.facebook_url}}{{ site.facebook_username }}">
        <span class="icon icon--facebook">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
            <img src="/assets/images/socialnetwork/facebook_32.png"/>
          </svg>
        </span>
        <span class="username">{{ site.facebook_username }}</span>
      </a>
    {% endif %}
    {% if site.instagram_username %}
      <a href="{{site.instagram_url}}{{ site.instagram_username }}">
        <span class="icon icon--instagram">
          <svg viewBox="0 0 16 16" width="16px" height="16px">
            <img src="/assets/images/socialnetwork/instagram_32.png"/>
          </svg>
        </span>
        <span class="username">{{ site.instagram_username }}</span>
      </a>
    {% endif %}
  </ul>
</div>
