<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>{% if page.title %}{{ page.title }}{% else %}{{ site.title }}{% endif %}</title>
  <meta name="description" content="{% if page.excerpt %}{{ page.excerpt | strip_html | strip_newlines | truncate: 160 }}{% else %}{{ site.description }}{% endif %}">
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

  <link rel="stylesheet" href="/assets/css/main.css">
  <link rel="canonical" href="{{ page.url | replace:'index.md','' | prepend: site.baseurl | prepend: site.url }}">
  <link rel="alternate" type="application/rss+xml" title="{{ site.title }}" href="{{ "/feed.xml" | prepend: site.baseurl | prepend: site.url }}" />
  <style type="text/css" media="screen">
    body {
      background-color: #f1f1f1;
      margin: 0;
      font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
    }
    .container { margin: 50px auto 40px auto; width: 600px; text-align: center; }
  </style>
</head>
