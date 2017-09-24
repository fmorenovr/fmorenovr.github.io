---
layout: post
title:  "Creating a VPS with Laravel and Apache service."
date:   2017-09-23 12:15:12 -0500
categories: Frameworks
---
# Install and prepare a PHP with Laravel Framework

* First, install LAMP lastest using taskel. You can find a tutorial [here][].

      sudo apt-get install php-mcrypt php-gd php-mbstring php7.0-pgsql

* Second, install Laravel framework:

      curl -sS https://getcomposer.org/installer | php
      sudo mv composer.phar /usr/local/bin/composer
      sudo chmod +x /usr/local/bin/composer

* Third, Create or Choose a file directory where is your public files and project:

      mkdir /home/user/your_website
      cd /home/user/your_website

* Fourth, here clone a laravel project from:

      git clone https://github.com/laravel/laravel.git

* Fifth, copy all files from `home/user/your_website/laravel` to `home/user/your_website/`:

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

      sudo chown www-data: -R /home/user/your_website/

## Adding with Apache

* Tenth, create a file conf for your website:

      sudo nano /etc/apache2/sites-available/your_website.conf

  Add these lines:
  
      <VirtualHost *:80>
        ServerAdmin admin@your_domain.com
        DocumentRoot /home/user/your_website/public/
        #ServerName your_domain.com
        #ServerAlias www.your_domain.com
        <Directory /home/user/your_website/>
          #Options FollowSymLinks
          AllowOverride All
          #Order allow,deny
          allow from all
        </Directory>
        ErrorLog /var/log/apache2/your_domain.com-error_log
        CustomLog /var/log/apache2/your_domain.com-access_log common
      </VirtualHost>
  
* Eleventh, enable the site and restart service:

      sudo a2ensite your_website.conf
      sudo service apache2 reload

* Twelfth, go to your workdirectory and run the service:

      php artisan serve


