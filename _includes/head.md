<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">

  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#157878">
  <link rel="shortcut icon" type="image/ico" href="{{site.url}}/assets/images/favicon.ico">
  
  <title>{% if page.title %}{{ page.title }}{% else %}{{ site.title }}{% endif %}</title>
  
  <link href='/assets/css/stylefonts.css' rel='stylesheet' type='text/css'>
  <link href='/assets/css/style.css' rel='stylesheet' type='text/css'>
  <link href='/assets/css/sidebar.css' rel='stylesheet' type='text/css'>
  <link href='/assets/css/navbar.css' rel='stylesheet' type='text/css'>
  <!--<link rel="stylesheet" href="{{ '/assets/css/style.css?v=' | append: site.github.build_revision | relative_url }}">-->
  <meta name="description"
    content="{% if page.excerpt %}{
      { page.excerpt | strip_html | strip_newlines | truncate: 160 }
      }{% else %}{
        { site.description }
      }{% endif %}">
  <link rel="alternate" type="application/rss+xml" title="{{ site.title }}" href="{{ "/feed.xml" | prepend: site.baseurl | prepend: site.url }}" />
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
  <link rel="canonical" href="{{ page.url | replace:'index.md','' | prepend: site.baseurl | prepend: site.url }}">  
</head>
