---
layout: post
title:  "HuGo, a setting up guide."
subtitle: Here you'll learn how to setup your Hugo serve, is very useful if you work with static pages.
date:   2018-04-05 00:20:12 -0500
categories: webServices
---
# Hugo

Is a simple blog, static site generator for personal projects.  
Hugo is written in Golang.  
See more info [here](http://gohugo.io/).

## Installing

For installing Hugo, we just need install some dependencies:

* Golang: Programming language, view my installation tutorial [here](/frameworks/Create-a-REST-service-using-Go-Language-and-BeeGo-Framework).

* Hugo:

      go get -v github.com/gohugoio/hugo

## Creating a static web

* If hugo exe doesnt generate, go to `$GOPATH/src/github.com/gohugoio/hugo` and run:

      go build -o hugo main.go

* Then, mv hugo binary to `go/bin` src.

Creating a new project on your local machine:

    hugo new site webApp
    
![hugo-new][hugo_new]

Note: by default hugo doesnt have theme, in other words, when you run `hugo serve`, it shows a blank page.

So, we need to install a theme to test hugo serve.

#### Themes

Then, download theme from repository:

    cd webApp/themes
    git clone https://github.com/saey55/hugo-elate-theme

Next, copy the file `themes/hugo-elate-theme/exampleSite/config.toml` to the current `config.toml`

You can look for more themes [here](https://themes.gohugo.io/).

## Serve

Finally, start the static web by default in port 1313:

    hugo serve

or, in a specific port and host (Note: if you use port 80 or 443, use sudo):

    sudo hugo serve --port 80 --bind localhost

![hugo-serve][hugo_serve]

In your favourite browser, enter to `localhost:1313`:

![hugo-localhost][hugo_localhost]


[hugo_new]:             /assets/webApp/hugo/hugo_new.png
[hugo_serve]:           /assets/webApp/hugo/hugo_serve.png
[hugo_localhost]:       /assets/webApp/hugo/hugo_localhost.png
