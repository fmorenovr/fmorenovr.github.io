---
layout: post
title:  "Creating a VPS with Laravel and Apache service."
date:   2017-09-23 12:15:12 -0500

tags:
  - VPS
  - Linux
  - Ubuntu
  - Virtual Private Server
  - Webserver
  - PHP
  - Laravel
  - Apache
  
categories:
  - Frameworks
---

Here you'll learn how to create your own VPS.

# Install and prepare a PHP with Laravel Framework

* First, install LAMP lastest using taskel. You can find a tutorial [here][tasksel-tuto].

      sudo apt-get install php-mcrypt php-gd php-mbstring php7.0-pgsql

* Second, install Laravel framework:

      curl -sS https://getcomposer.org/installer | php
      sudo mv composer.phar /usr/local/bin/composer
      sudo chmod +x /usr/local/bin/composer

* Third, Create or Choose a file directory where is your public files and project:

      mkdir /path/dir/your_website
      cd /path/dir/your_website

* Fourth, here clone a laravel project from:

      git clone https://github.com/laravel/laravel.git

* Fifth, copy all files from `/path/dir/your_website/laravel`:

      mv laravel/* .
      mv laravel/.* .

* Sixth, remove laravel directory:

      rm -rf laravel

* Seventh, go to your workdirectory and install php components with:

      composer install

* Eighth, create a `.env` file and key:

      touch .env
      php artisan key:generate

  Then, add this line on your `.env` file:
  
      APP_KEY=base64:wOYfq4yBb3OXt44asc54bOv4y71LHP0BQGn28D+5js=

* Ninth, assign permission to access:

      sudo chmod 777 -R /path/dir/your_website
      sudo chown -hR $USER:$USER /path/dir/your_website

## Adding with Apache

* Tenth, create a file `your_website.conf` for your website:

      sudo nano /etc/apache2/sites-available/your_website.conf

  Add these lines:
  
      <VirtualHost *:80>
        ServerAdmin admin@localhost
        DocumentRoot /path/dir/your_website/public/
        ServerName your_website.com
        #ServerAlias www.your_domain.com
        <Directory /path/dir/your_website/>
          #Options FollowSymLinks
          AllowOverride All
          #Order allow,deny
          allow from all
        </Directory>
        ErrorLog /var/log/apache2/your_domain.com-error_log
        CustomLog /var/log/apache2/your_domain.com-access_log common
      </VirtualHost>

  And modifiy in `/etc/apache2/apache2.conf`:
  
      <Directory /path/dir/your_website>
          Options Indexes FollowSymLinks
          AllowOverride All
          Require all granted
      </Directory>
  
* Eleventh, enable the site and restart service:

      sudo a2dissite 000-default.conf
      sudo a2ensite your_website.conf
      sudo service apache2 reload
      sudo a2enmod rewrite
      sudo service apache2 restart

* Twelfth, if you would like to run in local, go to your workdirectory and run the service (by default, run in port 8000):

      sudo php artisan serve --port 80
      php artisan serve

[tasksel-tuto]:  /software-bundles/Using-Tasksel_to_install_LAMP_server
