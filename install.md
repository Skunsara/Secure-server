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
