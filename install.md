## 13/07/2023 - 28/07/2023
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

Check if UFW (Uncomplicated Firewall) is installed on your system by running the following command:

sudo ufw status
you can install it by running:

sudo apt-get install ufw

Disable all incoming connections by default:
sudo ufw default deny incoming

Allow SSH connections:
sudo ufw allow ssh

Allow HTTPS connections:
sudo ufw allow https

Enable the firewall to start protecting your VM:
sudo ufw enable

Confirm the firewall status to verify that only SSH and HTTPS are allowed:
sudo ufw status

Installation Fail2ban with the command :
sudo apt install fail2ban & sudo apt upgrade

Creation a local configuration file to override the defaults and make any customizations. Create the local configuration file:
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
-sudo nano /etc/fail2ban/jail.local
[all_ports]
enabled = true
port = all
filter = all_ports
logpath = /var/log/syslog
maxretry = 5
bantime = 1d
[sshd]
mode   = aggressive
port    = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s
bantime = 1d
maxretry = 3

Enable Fail2ban
sudo systemctl enable fail2ban

Start Fail2ban:
sudo systemctl start fail2ban
