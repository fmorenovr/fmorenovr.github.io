---
layout: post
title:  "Config and Setting up your crontab File."
subtitle: Here you will learn how to config crontab file in your OS Linux system.
date:   2018-03-22 11:55:12 -0500
categories: Config
---
## Cron

Cron is a process admin that running as a deamon process in background.  
Cron can execute commands at specific times or in an interval of time (periods) for example, execute "hello world" every 5 minutes.

Cron in greek means **time**.

## Crontab

Each user in linux systems have Crontab file stored in `/etc/` directory.  
Users enable to create their crontab file is specified in the `cron.allow` file and Users disable to create is specified in the `cron.deny` file.

Each line in crontab file is a CRON expression for example:

```
  SHELL=/bin/bash
  PATH=/sbin:/bin:/usr/sbin:/usr/bin
  MAILTO=root
  HOME=/

  # run-parts
  
  .--------------- minute (0-59) 
  |  .------------ hour (0-23)
  |  |  .--------- day of month (1-31)
  |  |  |  .------ month (1-12) o jan,feb,mar,apr,may,jun,jul... (meses en inglés)
  |  |  |  |  .--- day of week (0-6) (sunday=0 ó 7) o sun,mon,tue,wed,thu,fri,sat 
  |  |  |  |  |
  *  *  *  *  *  command to execute
  01 *  *  *  *  root nice -n 19 run-parts /etc/cron.hourly
  50 0  *  *  *  root nice -n 19 run-parts /etc/cron.daily
  22 4  *  *  0  root nice -n 19 run-parts /etc/cron.weekly
  42 4  1  *  *  root nice -n 19 run-parts /etc/cron.monthly
```

## Args for Crontab

* Specifies the crontab user file

      crontab [ -u usuario ] file

* Adding other commands to crontab

      crontab [ -u usuario ] { -l | -r | -e }

    * `-u` specifies user that we want to admin, only root user can use this.  
    * `-e` edit the crontab file.  
    * `-l` list the active crontab entries.  
    * `-r` delete crontab.  
    
## Special commands for Crontab

* This commands abreviates text.

      @reboot  #Runs at boot
      @yearly  #Runs once a year   [0 0 1 1 *]
      @annually  #Runs once a year [0 0 1 1 *]
      @monthly  #Runs once a month [0 0 1 * *]
      @weekly  #Runs once a week   [0 0 * * 0]
      @daily  #Runs once a day     [0 0 * * *]
      @midnight  #Runs once a day  [0 0 * * *]
      @hourly  #Runs once an hour  [0 * * * *]

### Examples

* In this example, you can programe a download every day at 21:30

      30 21 * * * cd /path/to/download/; wget http://example.com/file_to_download.extension

* Execute at boot (start mongod service):

      @reboot mongod -f /etc/mongod.conf &
