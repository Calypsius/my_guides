# LAMP
### at first we need update system
```
sudo apt-get update && apt-get upgrade -y
```
### create user
```
adduser username
```
### give sudo permission
```
usermod -aG sudo username
```
### enable ufw
```
sudo ufw allow 'OpenSSH'
```
```
sudo ufw enable
```
```
sudo ufw status
```
### change user
```
su username
```
### install need applications
```
sudo apt-get install apache2 mysql-server php libapache2-mod-php php-mysql -y
```
### to conf mysql
```
sudo mysql
```
```
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
```
```
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
```
### open 80/443 ports
```
sudo ufw allow 'Apache Full'
```
### create folder for site
```
sudo mkdir /var/www/yourfolder
```
### change permission
```
sudo chown -R $USER:$USER /var/www/yourfolder
```
### conf for website
```
sudo nano /etc/apache2/sites-available/yourfolder.conf
```
```
<VirtualHost *:80>
        ServerName domain or ip
        DocumentRoot /var/www/yourfolder
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
### activate conf
```
sudo a2ensite yourfolder.conf
```
### deactivate default conf
```
sudo a2dissite 000-default.conf
```
### restart apache
```
sudo systemctl reload apache2
```
### and move your file in /var/www/yourfolder and open
```
http://your ip or domain
```