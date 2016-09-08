# cc

CC drupal and CiviCRM integration site
<br>
sudo apt-get update
<br>

cd /tmp/ && wget http://nginx.org/keys/nginx_signing.key
<br>
sudo apt-key add nginx_signing.key
<br>

sudo vi /etc/apt/sources.list.d/nginx.list
<br>
deb http://nginx.org/packages/mainline/ubuntu/ trusty nginx
<br>
deb-src http://nginx.org/packages/mainline/ubuntu/ trusty nginx
<br>

sudo apt-get update && sudo apt-get install nginx
<br>


This step is then corrected in puppet code. Originally placed in sites-available and linked in sites-enabled
<br>
Change /etc/nginx/conf.d/default.nginx.conf
<br>
Change /etc/nginx/conf.d/default-ssl.nginx.conf
<br>

In current site 
<br>
Change /etc/nginx/sites-available/default
<br>
ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default
<br>

<br>
Change /etc/nginx/sites-available/default-ssl
<br>
ln -s /etc/nginx/sites-available/default-ssl /etc/nginx/sites-enabled/default-ssl

<br>
sudo add-apt-repository ppa:ondrej/php5
<br>
sudo apt-get install python-software-properties
<br>
sudo apt-get install php-pear php5 php5-cli php5-common php5-curl php5-fpm php5-gd php5-json php5-mcrypt php5-mysql php5-readline
<br>

sudo apt-get install mysql-server mysql-client
<br>

mysql server root password is "123456"
<br>

References consulted.
<br>
https://wiki.civicrm.org/confluence/display/CRMDOC/CiviCRM+PHP+Requirements
<br>
https://wiki.civicrm.org/confluence/display/CRMDOC/Installation+and+Upgrades
<br>
http://redcrackle.com/blog/how-install-drupal-7-nginx-php-fpm-and-mysql-ubuntu-1404
<br>
https://www.liberiangeek.net/2014/10/install-latest-version-nginx-ubuntu-14-10/
<br>
https://www.dev-metal.com/how-to-setup-latest-version-of-php-5-5-on-ubuntu-12-04-lts/
<br>


create database drupal_cvc;
<br>
create user 'drupaluser_cvc'@'localhost' identified by 'drplcvc2016';
<br>
use drupal_cvc;
<br>
grant all on drupal_cvc.* to 'drupaluser_cvc'@'localhost';
<br>

table prefix : cvc_
<br>

cd /usr/share/nginx
<br>
rm -rf html
<br>
sudo wget https://ftp.drupal.org/files/projects/drupal-7.38.tar.gz
<br>
sudo tar -xvzf drupal-7.38.tar.gz
<br>
sudo sudo mv drupal-7.38 html
<br>
<br>

cd /usr/share/nginx/html/sites/default
<br>
sudo mkdir files
<br>
sudo chown -R www-data files
<br>
sudo cp default.settings.php settings.php
<br>
sudo chmod 777 settings.php
<br>

Change server in upstream to 
<br>
unix:/var/run/php5-fpm.sock;
<br>

Admin Username : civicrm_admin
<br>
Admin Password : C1v1crmAdm1n!
<br>

sudo bash drush_install.sh
<br>
sudo apt-get install git-all
<br>

mkdir /mnt/private_file_folder
<br>
chowm -R www-data: /mnt/private_file_folder
<br>
chowm -R www-data: /var/share/nginx/html
<br>


Location of civiCRM https://download.civicrm.org/civicrm-4.7.10-drupal.tar.gz
<br>
install module in modules page of drupal

<br>
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES, TRIGGER, CREATE ROUTINE, ALTER ROUTINE ON civicrm.* TO 'civicrm_user'@'localhost' IDENTIFIED BY 'cvcrm2016';

<br>
GRANT SELECT on drupal_cvc.* to 'civicrm_user'@'localhost' ;

<br>
installed from /sites/all/modules/civicrm/install/index.php


<br>
http://52.72.130.54/civicrm/admin/setting/uf?reset=1

References consulted.
<br>
https://github.com/puppetlabs/puppetlabs-aws
<br>
https://puppet.com/blog/provision-aws-infrastructure-using-puppet
<br>
https://www.digitalocean.com/community/tutorials/how-to-install-puppet-4-in-a-master-agent-setup-on-ubuntu-14-04
<br>
https://www.digitalocean.com/community/tutorials/how-to-install-puppet-4-in-a-master-agent-setup-on-ubuntu-14-04
<br>


Reference for backup to S3 bucket
<br>
https://www.drupal.org/node/2465951
<br>

My created user for backup. 
<br>
ccbackup_user

<br>


