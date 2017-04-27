<footer class="site-footer">
  <div class="wrapper">
    <div class="footer-col-wrapper">
      <div class="footer-col footer-col-1">
        <ul class="contact-list">
          <li> Email me: </li>
          {% if site.author.email %}
            <a href="mailto:{{ site.author.email }}">
              <span class="icon icon--email">
                <svg viewBox="0 0 16 16" width="16px" height="16px">
                  <path d="M7,9L5.268,7.484l-4.952,4.245C0.496,11.896,0.739,12,1.007,12h11.986 c0.267,0,0.509-0.104,0.688-0.271L8.732,7.484L7,9z M13.684,2.271C13.504,2.103,13.262,2,12.993,2H1.007C0.74,2,0.498,2.104,0.318,2.273L7,8 L13.684,2.271z"/>
                  <polygon points="0,2.878 0,11.186 4.833,7.079"/>
                  <polygon points="9.167,7.079 14,11.186 14,2.875"/>
                </svg>
              </span>
              <span class="email">Felipe Moreno</span>
            </a>&nbsp;
          {% endif %}
          <!--<li><a href="mailto:felipe.moreno.vera@gmail.com">felipe.moreno.v@uni.pe</a></li>-->
        </ul>
      </div>
      <div class="footer-col footer-col-2">
        <ul class="social-media-list">
          {% if site.linkedin_username %}
            <li>
              <a href="https://linkedin.com/in/{{ site.linkedin_username }}">
                <span class="icon icon--linkedin">
                  <svg viewBox="0 0 16 16" width="16px" height="16px">
                    {% if page.layout != "post"%}
                      <img src="../assets/imgs/socialnetwork/linkedin.png"/>
                    {% else %}
                      <img src="../../../../../assets/imgs/socialnetwork/linkedin.png"/>
                    {% endif %}
                  </svg>
                </span>
                <span class="username">{{ site.linkedin_username }}</span>
              </a>
            </li>
          {% endif %}
          {% if site.github_username %}
            <li>
              <a href="https://github.com/{{ site.github_username }}">
                <span class="icon icon--github">
                  <svg viewBox="0 0 16 16" width="16px" height="16px">
                    {% if page.layout != "post"%}
                      <img src="../assets/imgs/socialnetwork/github.png"/>
                    {% else %}
                      <img src="../../../../../assets/imgs/socialnetwork/github.png"/>
                    {% endif %}
                  </svg>
                </span>
                <span class="username">{{ site.github_username }}</span>
              </a>
            </li>
          {% endif %}
          {% if site.bitbucket_username %}
            <li>
              <a href="https://bitbucket.org/{{ site.bitbucket_username }}">
                <span class="icon icon--bitbucket">
                  <svg viewBox="0 0 16 16" width="16px" height="16px">
                    {% if page.layout != "post"%}
                      <img src="../assets/imgs/socialnetwork/bitbucket.png"/>
                    {% else %}
                      <img src="../../../../../assets/imgs/socialnetwork/bitbucket.png"/>
                    {% endif %}
                  </svg>
                </span>
                <span class="username">{{ site.bitbucket_username }}</span>
              </a>
            </li>
          {% endif %}
          {% if site.facebook_username %}
            <li>
              <a href="https://www.facebook.com/{{ site.facebook_username }}">
                <span class="icon icon--facebook">
                  <svg viewBox="0 0 16 16" width="16px" height="16px">
                    {% if page.layout != "post"%}
                      <img src="../assets/imgs/socialnetwork/facebook.png"/>
                    {% else %}
                      <img src="../../../../../assets/imgs/socialnetwork/facebook.png"/>
                    {% endif %}
                  </svg>
                </span>
                <span class="username">{{ site.facebook_username }}</span>
              </a>
            </li>
          {% endif %}
          {% if site.twitter_username %}
            <li>
              <a href="https://twitter.com/{{ site.twitter_username }}">
                <span class="icon icon--twitter">
                  <svg viewBox="0 0 16 16" width="16px" height="16px">
                    {% if page.layout != "post"%}
                      <img src="../assets/imgs/socialnetwork/twitter.png"/>
                    {% else %}
                      <img src="../../../../../assets/imgs/socialnetwork/twitter.png"/>
                    {% endif %}
                  </svg>
                </span>
                <span class="username">{{ site.twitter_username }}</span>
              </a>
            </li>
          {% endif %}
          </ul>
      </div>
      <div class="footer-col footer-col-3">
        <p class="text">{{ site.description }}</p>
      </div>
    </div>
  </div>
</footer>
