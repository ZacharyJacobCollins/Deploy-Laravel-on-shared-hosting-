# Update
  sudo apt-get update && apt-get install vim && apt-get install git && apt-get install php7.0-sqlite3


# new user
  adduser username
  usermod -aG sudo username

# installing node correctly need 6.9>
http://yoember.com/nodejs/the-best-way-to-install-node-js/


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






  



SSL ENABLED


    # HTTPS — proxy all requests to the Node app
    server {
        # Enable HTTP/2
        listen 443 ssl http2;
        listen [::]:443 ssl http2;
        server_name app.example.com;

        # Use the Let’s Encrypt certificates
        ssl_certificate /etc/letsencrypt/live/app.example.com/fullchain.pem;
        ssl_certificate_key /etc/letsencrypt/live/app.example.com/privkey.pem;

        # Include the SSL configuration from cipherli.st
        include snippets/ssl-params.conf;

        location / {
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-NginX-Proxy true;
            proxy_pass http://localhost:5000/;
            proxy_ssl_session_reuse off;
            proxy_set_header Host $http_host;
            proxy_cache_bypass $http_upgrade;
            proxy_redirect off;
        }
    }
    
    
    
    

