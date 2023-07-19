## 13/07/2023 
Creation of usernames for each user: amin, maikl, michel using the command "adduser amin", etc.

Updating the repository with the commands "apt update" and "apt upgrade".

Installing Apache with the command "apt-get install apache2".

Installing MySQL with the command "apt-get install mysql-server".

Setting up the encrypted password for SQL.

Installing PHP with the command "apt-get install php".

CREATION MYSQL TABLE with "CREATE DATABASE wikidb"

CREATION USER MYSQL with "CREATE USER 'new_mysql_user'@'localhost' IDENTIFIED BY 'PASSWORD';"

Gave permission to this user to edit the file with "GRANT ALL ON wikidb.* TO 'new_mysql_user'@'localhost';"

Navigate to the Apache configuration directory. The exact path may vary depending on your server's configuration, but it is typically located at /etc/apache2/sites-available/.

sudo nano /etc/apache2/sites-available/wiki.conf (you can see wiki.conf in github)

Disable the default Apache site:
sudo a2dissite 000-default.conf 

Enable the wiki.conf configuration:
sudo a2ensite wiki.conf

restart the Apache service:
sudo service apache2 restart

to see if there any error on the apache service
sudo service apache2 status

"Invalid command 'SSLEngine',error on Apache

To resolve this issue, you need to enable the SSL module in Apache. You can do this by running the following command:

sudo a2enmod ssl

After enabling the SSL module, restart the Apache service:

sudo service apache2 restart

