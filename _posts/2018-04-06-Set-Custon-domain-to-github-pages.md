---
layout: post
title:  "Setting up a static website and set custom domain."
date:   2018-04-06 11:55:12 -0500

tags:
  - Github
  - Git
  - Github Pages
  - webservices
  - websites
  - web domain
  - markdown
  
categories:
  - Software
---

Here you will learn how to create and config your CNAME in your github page.

## Github Pages

Github offers you the possibility to create a static webpage for your user account.  
More info [here](https://guides.github.com/features/pages/) or [here](https://pages.github.com/).

## Static web

To create a static web supported by github or bitbucket or gitlab, etc.  
You should choose which framework do you like more (jekyll, hugo, etc).  
In my case, my static website is in Jekyll, my [website](http://www.jenazads.com) created as Jenazads username with the template cayman.

* View a tutorial with jekyll [here](/webservices/Jekyll-a-setting-up-guide).  
* View a tutorial with hugo [here](/webservices/Hugo-a-setting-up-guide).  

## Domains and DNS

Once you have finished to set up your own website, you would able to change your domain (e.g. your url is **username.github.io**) to personalized url.

In my case, I use Amazon Route 53 service to buy a domain and dns servers.

* Just login to amazon account and select Route 53.

  ![aws-services](/assets/internet_services/AWS/aws-services.png)

* Then, search for the domain that you looking for:

  note that: **.com** is for commercial purpose and **.org** is for non-profit purpose.

  ![aws-route](/assets/internet_services/AWS/aws-route-domainSearch.png)

* Once, you registered and buyed your domain you can manage DNS and subdomains in the console:

  ![aws-domains](/assets/internet_services/AWS/aws-domains.png)

* Next, You could manage your DNS and subdomains, creates, delete subdomains as you whish.

* For this example, we will work with **yourdomain.com**.

## Custom domain git pages

Once you have bought your domain and your static web is enable already, go to your username.github.io project settings (in this case is in github, that name could be different if you use bitbucket or gitlab).

Once in settings, search for the option github pages.

  ![github-pages-domain](/assets/systemVersionSoftware/Git/repo_custom_domain_github.png)

Set **yourdomain.com** in the option custom domain or just create a CNAME file in the root folder of your website project.

### Why not www ?

No www. needed. If you do put **www.yourdomain.com** github will figure out and redirect properly nevertheless, as explained [here](https://help.github.com/articles/using-a-custom-domain-with-github-pages/). The difference is **yourdomain.com** is a top-level domain (TLD), while **www.yourdomain.com** is a subdomain.  
A better explanation could be found [here](https://help.github.com/articles/setting-up-an-apex-domain/).

## Create domains and subdomains

* First, Create a Record set of type A (Ipv4 Address) and set your username.github.io ip address.  
  Or set your Ip Address as:
  
      192.30.252.153
      192.30.252.154
  
* Then create another CNAME record redirecting **www.yourdomain.com** to username.github.io, the original Github blog address.

Your final dns manage must be like this:

![dns-domains](/assets/internet_services/AWS/aws-dns-record-manage.png)

## Set Mail Service

You should be able to set up a mail service with [Amazon SES][SES] o [GSuite service][GSuite].

I use Gsuite, so you should create an admin account in GSuite and then write the IP Addresses in your Domain in Amazon Route 53 as like below:

![mail-domain](/assets/internet_services/AWS/aws-route-domain-mail.png)

## Notes

You can change your domain every time that you want.  
Have fun :D


[SES]:    https://aws.amazon.com/es/ses/
[GSuite]: https://gsuite.google.com/
