# Update
  sudo apt-get update

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
  
