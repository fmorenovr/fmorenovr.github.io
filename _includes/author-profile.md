{% include base_path %}

{% if page.author and site.data.authors[page.author] %}
  {% assign author = site.data.authors[page.author] %}{% else %}{% assign author = site.author %}
{% endif %}

<div itemscope itemtype="http://schema.org/Person">

  <div class="author__avatar">
    {% if author.avatar contains "://" %}
    	<img src="{{ author.avatar }}" alt="{{ author.name }}">
    {% else %}
    	<img src="{{ author.avatar | prepend: "/assets/images/" | prepend: base_path }}" class="author__avatar" alt="{{ author.name }}">
    {% endif %}
  </div>

  <!--<div class="author__content">
    <h3 class="author__name">{{ author.name }}</h3>
    {% if author.bio %}<p class="author__bio">{{ author.bio }}</p>{% endif %}
  </div>-->

  <div class="author__urls-wrapper">
    <button class="btn btn--inverse">Follow</button>
    <ul class="author__urls social-icons">
      <!--{% if author.employer %}
        <li><svg style="width: 16px;" class="octicon octicon-organization" viewBox="0 0 16 16" version="1.1" width="16" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M16 12.999c0 .439-.45 1-1 1H7.995c-.539 0-.994-.447-.995-.999H1c-.54 0-1-.561-1-1 0-2.634 3-4 3-4s.229-.409 0-1c-.841-.621-1.058-.59-1-3 .058-2.419 1.367-3 2.5-3s2.442.58 2.5 3c.058 2.41-.159 2.379-1 3-.229.59 0 1 0 1s1.549.711 2.42 2.088C9.196 9.369 10 8.999 10 8.999s.229-.409 0-1c-.841-.62-1.058-.59-1-3 .058-2.419 1.367-3 2.5-3s2.437.581 2.495 3c.059 2.41-.158 2.38-1 3-.229.59 0 1 0 1s3.005 1.366 3.005 4z"></path></svg> {{ author.employer }}</li>
      {% endif %}
      {% if author.location %}
        <li><svg style="width: 16px;" class="octicon octicon-location" viewBox="0 0 12 16" version="1.1" width="12" height="16" aria-hidden="true"><path fill-rule="evenodd" d="M6 0C2.69 0 0 2.5 0 5.5 0 10.02 6 16 6 16s6-5.98 6-10.5C12 2.5 9.31 0 6 0zm0 14.55C4.14 12.52 1 8.44 1 5.5 1 3.02 3.25 1 6 1c1.34 0 2.61.48 3.56 1.36.92.86 1.44 1.97 1.44 3.14 0 2.94-3.14 7.02-5 9.05zM8 5.5c0 1.11-.89 2-2 2-1.11 0-2-.89-2-2 0-1.11.89-2 2-2 1.11 0 2 .89 2 2z"></path></svg> {{ author.location }}</li>
      {% endif %}-->
      {% if author.email %}
        <li><a href="mailto:{{ author.email }}"><i class="fas fa-fw fa-envelope" aria-hidden="true"></i> {{ site.data.ui-text[site.locale].email_label | default: "Email" }}</a></li>
      {% endif %}
      {% if author.github %}
        <li><a href="https://github.com/{{ author.github }}"><i class="fab fa-fw fa-github" aria-hidden="true"></i> Github</a></li>
      {% endif %}
      {% if author.googlescholar %}
        <li><a href="https://scholar.google.com/citations?user={{ author.googlescholar }}"><i class="fas fa-fw fa-graduation-cap"></i> Google Scholar</a></li>
      {% endif %}
      <!--
      {% if author.arxiv %}
        <li><a href="https://arxiv.org/a/{{ author.arxiv }}"><i class="ai ai-fw ai-arxiv-square"></i> ARXIV</a></li>
      {% endif %}
      {% if author.orcid %}
        <li><a href="https://orcid.org/{{ author.orcid }}"><i class="ai ai-fw ai-orcid-square"></i> ORCID</a></li>
      {% endif %}
      {% if author.linkedin %}
        <li><a href="https://www.linkedin.com/in/{{ author.linkedin }}"><i class="fab fa-fw fa-linkedin" aria-hidden="true"></i> LinkedIn</a></li>
      {% endif %}
      {% if author.facebook %}
        <li><a href="https://www.facebook.com/{{ author.facebook }}"><i class="fab fa-fw fa-facebook-square" aria-hidden="true"></i> Facebook</a></li>
      {% endif %}
      {% if author.instagram %}
        <li><a href="https://instagram.com/{{ author.instagram }}"><i class="fab fa-fw fa-instagram" aria-hidden="true"></i> Instagram</a></li>
      {% endif %}
      {% if author.twitter %}
        <li><a href="https://twitter.com/{{ author.twitter }}"><i class="fab fa-fw fa-twitter-square" aria-hidden="true"></i> Twitter</a></li>
      {% endif %}
      {% if author.dina %}
        <li><a href="https://dina.concytec.gob.pe/appDirectorioCTI/VerDatosInvestigador.do?id_investigador={{ author.dina }}"><i class="fab fa-fw fa-dina-square"></i> DINA</a></li>
      {% endif %}
      
      {% if author.keybase %}
        <li><a href="https://keybase.io/{{ author.keybase }}"><i class="fas fa-fw fa-key" aria-hidden="true"></i> Keybase</a></li>
      {% endif %}
       {% if author.researchgate %}
        <li><a href="{{ author.researchgate }}"><i class="fab fa-fw fa-researchgate" aria-hidden="true"></i> ResearchGate</a></li>
      {% endif %}
      {% if author.uri %}
        <li><a href="{{ author.uri }}"><i class="fas fa-fw fa-link" aria-hidden="true"></i> {{ site.data.ui-text[site.locale].website_label | default: "Website" }}</a></li>
      {% endif %}
      {% if author.google_plus %}
        <li><a href="https://plus.google.com/+{{ author.google_plus }}"><i class="fab fa-fw fa-google-plus" aria-hidden="true"></i> Google+</a></li>
      {% endif %}
      {% if author.xing %}
        <li><a href="https://www.xing.com/profile/{{ author.xing }}"><i class="fab fa-fw fa-xing-square" aria-hidden="true"></i> XING</a></li>
      {% endif %}
      {% if author.tumblr %}
        <li><a href="https://{{ author.tumblr }}.tumblr.com"><i class="fab fa-fw fa-tumblr-square" aria-hidden="true"></i> Tumblr</a></li>
      {% endif %}
      {% if author.bitbucket %}
        <li><a href="https://bitbucket.org/{{ author.bitbucket }}"><i class="fab fa-fw fa-bitbucket" aria-hidden="true"></i> Bitbucket</a></li>
      {% endif %}
      {% if author.stackoverflow %}
        <li><a href="https://www.stackoverflow.com/users/{{ author.stackoverflow }}"><i class="fab fa-fw fa-stack-overflow" aria-hidden="true"></i> Stackoverflow</a></li>
      {% endif %}
      {% if author.lastfm %}
        <li><a href="https://lastfm.com/user/{{ author.lastfm }}"><i class="fab fa-fw fa-lastfm-square" aria-hidden="true"></i> Last.fm</a></li>
      {% endif %}
      {% if author.dribbble %}
        <li><a href="https://dribbble.com/{{ author.dribbble }}"><i class="fab fa-fw fa-dribbble-square" aria-hidden="true"></i> Dribbble</a></li>
      {% endif %}
      {% if author.pinterest %}
        <li><a href="https://www.pinterest.com/{{ author.pinterest }}"><i class="fab fa-fw fa-pinterest" aria-hidden="true"></i> Pinterest</a></li>
      {% endif %}
      {% if author.foursquare %}
        <li><a href="https://foursquare.com/{{ author.foursquare }}"><i class="fab fa-fw fa-foursquare" aria-hidden="true"></i> Foursquare</a></li>
      {% endif %}
      {% if author.steam %}
        <li><a href="https://steamcommunity.com/id/{{ author.steam }}"><i class="fab fa-fw fa-steam-square" aria-hidden="true"></i> Steam</a></li>
      {% endif %}
      {% if author.youtube %}
        <li><a href="https://www.youtube.com/user/{{ author.youtube }}"><i class="fab fa-fw fa-youtube" aria-hidden="true"></i> YouTube</a></li>
      {% endif %}
      {% if author.soundcloud %}
        <li><a href="https://soundcloud.com/{{ author.soundcloud }}"><i class="fab fa-fw fa-soundcloud" aria-hidden="true"></i> Soundcloud</a></li>
      {% endif %}
      {% if author.weibo %}
        <li><a href="https://www.weibo.com/{{ author.weibo }}"><i class="fab fa-fw fa-weibo" aria-hidden="true"></i> Weibo</a></li>
      {% endif %}
      {% if author.flickr %}
        <li><a href="https://www.flickr.com/{{ author.flickr }}"><i class="fab fa-fw fa-flickr" aria-hidden="true"></i> Flickr</a></li>
      {% endif %}
      {% if author.codepen %}
        <li><a href="https://codepen.io/{{ author.codepen }}"><i class="fab fa-fw fa-codepen" aria-hidden="true"></i> CodePen</a></li>
      {% endif %}
      {% if author.vine %}
        <li><a href="https://vine.co/u/{{ author.vine }}"><i class="fab fa-fw fa-vine" aria-hidden="true"></i> Vine</a></li>
      {% endif %}
      {% if author.pubmed %}
        <li><a href="{{ author.pubmed }}"><i class="ai ai-pubmed-square ai-fw"></i> PubMed</a></li>
      {% endif %}
      {% if author.impactstory %}
        <li><a href="{{ author.impactstory }}"><i class="ai ai-impactstory ai-fw"></i> Impactstory</a></li>
      {% endif %}
      {% if author.wikipedia %}
        <li><a href="https://en.wikipedia.org/wiki/User:{{ author.wikipedia }}"><i class="fab fa-fw fa-wikipedia-w" aria-hidden="true"></i> Wikipedia</a></li>
      {% endif %}
      -->
    </ul>
  </div>
</div>
