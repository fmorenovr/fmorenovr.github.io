<div class="container text-center">
  <ul class="contact-list">
    <li> Email me: </li>
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
<div class="container text-center">
  <li> Contact to me: </li>
  <ul class="social-media-list">
    {% if site.github_username %}
      <li>
        <a href="https://github.com/{{ site.github_username }}">
          <span class="icon icon--github">
            <svg viewBox="0 0 16 16" width="16px" height="16px">
              {% if page.layout != "post"%}
                <img src="../assets/imgs/socialnetwork/github_32.png"/>
              {% else %}
                <img src="../../../../../assets/imgs/socialnetwork/github_32.png"/>
              {% endif %}
            </svg>
          </span>
          <span class="username">{{ site.github_username }}</span>
        </a>
      </li>
    {% endif %}
    {% if site.linkedin_username %}
      <li>
        <a href="https://linkedin.com/in/{{ site.linkedin_username }}">
          <span class="icon icon--linkedin">
            <svg viewBox="0 0 16 16" width="16px" height="16px">
              {% if page.layout != "post"%}
                <img src="../assets/imgs/socialnetwork/linkedin_32.png"/>
              {% else %}
                <img src="../../../../../assets/imgs/socialnetwork/linkedin_32.png"/>
              {% endif %}
            </svg>
          </span>
          <span class="username">{{ site.linkedin_username }}</span>
        </a>
      </li>
    {% endif %}
    {% if site.facebook_username %}
      <li>
        <a href="https://www.facebook.com/{{ site.facebook_username }}">
          <span class="icon icon--facebook">
            <svg viewBox="0 0 16 16" width="16px" height="16px">
              {% if page.layout != "post"%}
                <img src="../assets/imgs/socialnetwork/facebook_32.png"/>
              {% else %}
                <img src="../../../../../assets/imgs/socialnetwork/facebook_32.png"/>
              {% endif %}
            </svg>
          </span>
          <span class="username">{{ site.facebook_username }}</span>
        </a>
      </li>
    {% endif %}
  </ul>
</div>
<div class="container text-center">
  <p> Copyright &copy; Felipe A. Moreno ~ 2017</p>
</div>
