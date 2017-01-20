# Update
  sudo apt-get update && apt-get install vim && apt-get install git

# new user
  adduser username
  usermod -aG sudo username


#PHP and extensions
  sudo apt-get install php
  sudo apt-get install php7.0-zip
  sudo apt-get install php7.0-fpm 
  sudo apt-get install php7.0-mbstring
  sudo apt-get install php7.0-xml 
  sudo apt-get install php7.0-curl
  
#Composer
  sudo apt-get install composer
  
#Laravel
  sudo apt-get install
  composer global require "laravel/installer"
  
#New project
  composer create-project --prefer-dist laravel/laravel blog
  
#Working nginx conf
** NOTE COPY TO BOTH SITES-ENABLED AND SITES-AVAILABLE
  
    server {
      listen 80 default_server;
      listen [::]:80 default_server;

      root /var/www/html/laravel/public;
      index index.php index.html index.htm index.nginx-debian.html

      server_name SERVER_IP_ADDRESS_GOES_HERE;

      location / {
        try_files $uri $uri/ /index.php?$query_string =404;
      }    

      location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/run/php/php7.0-fpm.sock;
      }

      location ~ /\.ht {
        deny all;
      }
    }






  
