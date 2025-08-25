# Wordpress-Commands

YouTube video link: https://youtu.be/8Uofkq718n8
All the commands that are executed in the above youtube video are mentioned in this gist. 

1. Install Apache server on Ubuntu
sudo apt install apache2

2. Install php runtime and php mysql connector
sudo apt install php libapache2-mod-php php-mysql

3. Install MySQL server
sudo apt install mysql-server 

4. Login to MySQL server
sudo mysql -u root

5. Change authentication plugin to mysql_native_password (change the password to something strong)
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'Testpassword@123';

6. Create a new database user for wordpress (change the password to something strong)
CREATE USER 'wp_user'@localhost IDENTIFIED BY 'Testpassword@123';

7. Create a database for wordpress
CREATE DATABASE wp;

8. Grant all privilges on the database 'wp' to the newly created user
GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@localhost;

9. Download wordpress
cd /tmp
wget https://wordpress.org/latest.tar.gz

10. Unzip
tar -xvf latest.tar.gz

11. Move wordpress folder to apache document root
sudo mv wordpress/ /var/www/html

12. Command to restart/reload apache server
sudo systemctl restart apache2
OR
sudo systemctl reload apache2

13. Install certbot
sudo apt-get update
sudo apt install certbot python3-certbot-apache

14. Request and install ssl on your site with certbot
sudo certbot --apache


// to configure the dns
15. cd /etc/apcache2/sites-available

16. open 000-default.conf
vi 000-default.conf

17. change the following ( DocumentRoot /var/www/html ) to
 DocumentRoot /var/www/html/wordpress

18. Command to restart/reload apache server
sudo systemctl restart apache2
OR
sudo systemctl reload apache2

19. to add the domain, follow this thing
add Alias like : 
ServerAdmin webmaster@localhost
DocumentRoot /var/www/html/wordpress
Alias "wordpress" "/var/www/html/wordpress"

And add the domain : 
