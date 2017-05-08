---
layout: post
title:  "Git, A Fast Guide for Newcomers."
date:   2017-05-07 00:20:12 -0500
categories: Version_System_Manager
---
# git

Git is a softwar controling version system, using logs, you can see all modification (named as commit) of your project.

    sudo apt-get install git

* For one local repository, on the actual dir:

      git config user.name "username"
      git config user.email "usermail"

* For all repositories on our machine:

      git config --global user.name "username"
      git config --global user.email "usermail"

* With git status, we check if there one update.

      git status
      git pull origin master
      git add .
      git commit -m "modificacion"
      git push origin master

* Configurate a local repository in `.git/config` add the fields

	    [remote "origin"]
		    url = https://github.com/path/repo.git
		    fetch = +refs/heads/*:refs/remotes/origin/*
