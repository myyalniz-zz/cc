# cc

The site has a DNS: http://www.cc2016test.com
It is redirected permanent to https://www.cc2016test.com
The Elastic IP assigned is 52.72.130.54

The key for ubuntu user is cc-test.pem and will be shared.

CC drupal and CiviCRM integration site
sudo apt-get update

cd /tmp/ && wget http://nginx.org/keys/nginx_signing.key
sudo apt-key add nginx_signing.key

sudo vi /etc/apt/sources.list.d/nginx.list
deb http://nginx.org/packages/mainline/ubuntu/ trusty nginx
deb-src http://nginx.org/packages/mainline/ubuntu/ trusty nginx

sudo apt-get update && sudo apt-get install nginx


# This step is then corrected in puppet code. Originally placed in sites-available and linked in sites-enabled
Change /etc/nginx/conf.d/default.nginx.conf
Change /etc/nginx/conf.d/default-ssl.nginx.conf

# In current site 
Change /etc/nginx/sites-available/default
ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default

Change /etc/nginx/sites-available/default-ssl
ln -s /etc/nginx/sites-available/default-ssl /etc/nginx/sites-enabled/default-ssl

sudo add-apt-repository ppa:ondrej/php5
sudo apt-get install python-software-properties
sudo apt-get install php-pear php5 php5-cli php5-common php5-curl php5-fpm php5-gd php5-json php5-mcrypt php5-mysql php5-readline

sudo apt-get install mysql-server mysql-client

mysql server root password is "123456"

# References consulted.
https://wiki.civicrm.org/confluence/display/CRMDOC/CiviCRM+PHP+Requirements
https://wiki.civicrm.org/confluence/display/CRMDOC/Installation+and+Upgrades
http://redcrackle.com/blog/how-install-drupal-7-nginx-php-fpm-and-mysql-ubuntu-1404
https://www.liberiangeek.net/2014/10/install-latest-version-nginx-ubuntu-14-10/
https://www.dev-metal.com/how-to-setup-latest-version-of-php-5-5-on-ubuntu-12-04-lts/


create database drupal_cvc;
create user 'drupaluser_cvc'@'localhost' identified by 'drplcvc2016';
use drupal_cvc;
grant all on drupal_cvc.* to 'drupaluser_cvc'@'localhost';

table prefix : cvc_

cd /usr/share/nginx
rm -rf html
sudo wget https://ftp.drupal.org/files/projects/drupal-7.38.tar.gz
sudo tar -xvzf drupal-7.38.tar.gz
sudo sudo mv drupal-7.38 html

cd /usr/share/nginx/html/sites/default
sudo mkdir files
sudo chown -R www-data files
sudo cp default.settings.php settings.php
sudo chmod 777 settings.php

Change server in upstream to 
unix:/var/run/php5-fpm.sock;

Admin Username : civicrm_admin
Admin Password : C1v1crmAdm1n!

sudo bash drush_install.sh
sudo apt-get install git-all

mkdir /mnt/private_file_folder
chowm -R www-data: /mnt/private_file_folder
chowm -R www-data: /var/share/nginx/html


Location of civiCRM https://download.civicrm.org/civicrm-4.7.10-drupal.tar.gz
install module in modules page of drupal

GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES, TRIGGER, CREATE ROUTINE, ALTER ROUTINE ON civicrm.* TO 'civicrm_user'@'localhost' IDENTIFIED BY 'cvcrm2016';

GRANT SELECT on drupal_cvc.* to 'civicrm_user'@'localhost' ;

installed from /sites/all/modules/civicrm/install/index.php


http://52.72.130.54/civicrm/admin/setting/uf?reset=1

# References consulted.
https://github.com/puppetlabs/puppetlabs-aws
https://puppet.com/blog/provision-aws-infrastructure-using-puppet
https://www.digitalocean.com/community/tutorials/how-to-install-puppet-4-in-a-master-agent-setup-on-ubuntu-14-04
https://www.digitalocean.com/community/tutorials/how-to-install-puppet-4-in-a-master-agent-setup-on-ubuntu-14-04


Reference for backup to S3 bucket
https://www.drupal.org/node/2465951

My created user for backup. 
ccbackup_user



