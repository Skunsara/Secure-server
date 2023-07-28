## 13/07/2023 - 28/07/2023
# User Creation:
#Creation of usernames for each user: amin, maikl, michel using the command 

adduser amin
adduser maikl
# System Updates and Package Installations:
#Updating the repository with the commands 

apt update & apt upgrade

#Installing Apache with the command 

apt-get install apache2
# MySQL Configuration:
#Installing MySQL with the command 

apt-get install mysql-server

#Setting up the encrypted password for SQL.

#Installing PHP with the command 

apt-get install php

#CREATION MYSQL TABLE with 

CREATE DATABASE wikidb

#CREATION USER MYSQL with 

CREATE USER 'new_mysql_user'@'localhost' IDENTIFIED BY 'PASSWORD';

#Gave permission to this user to edit the file with 

GRANT ALL ON wikidb.* TO 'new_mysql_user'@'localhost';
# Apache Configuration:
#Navigate to the Apache configuration directory. The exact path may vary depending on your server's configuration, but it is typically located at /etc/apache2/sites-available/.

sudo nano /etc/apache2/sites-available/wiki.conf (you can see wiki.conf in github)

#Disable the default Apache site:

sudo a2dissite 000-default.conf 

#Enable the wiki.conf configuration:

sudo a2ensite wiki.conf

#Restart the Apache service:

sudo service apache2 restart

#To see if there any error on the apache service

sudo service apache2 status

#"Invalid command 'SSLEngine',error on Apache

#To resolve this issue, you need to enable the SSL module in Apache. You can do this by running the following command:

sudo a2enmod ssl

#After enabling the SSL module, restart the Apache service:

sudo service apache2 restart
# Firewall (UFW) Configuration:
#Check if UFW (Uncomplicated Firewall) is installed on your system by running the following command:

sudo ufw status
#you can install it by running:

sudo apt-get install ufw

#Disable all incoming connections by default:

sudo ufw default deny incoming

#Allow SSH connections:

sudo ufw allow ssh

#Allow HTTPS connections:

sudo ufw allow https

#Enable the firewall to start protecting your VM:

sudo ufw enable

#Confirm the firewall status to verify that only SSH and HTTPS are allowed:

sudo ufw status
# Fail2ban Installation and Configuration:
#Installation Fail2ban with the command :

sudo apt install fail2ban & sudo apt upgrade

#Creation a local configuration file to override the defaults and make any customizations. Create the local configuration file:

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

#Enable Fail2ban

sudo systemctl enable fail2ban

#Start Fail2ban:

sudo systemctl start fail2ban

# Additional Network Configuration:
sudo nft add table inet filter
sudo nft add chain inet filter input { type filter hook input priority 0 \; }*

#The first rule accepts all traffic that is part of or related to an established connection. This is necessary for reply packets to get back to your system.

sudo nft add rule inet filter input ct state established,related accept

#The second rule accepts all traffic on the loopback interface. This is necessary for many applications to function properly.

sudo nft add rule inet filter input iifname lo accept

#The third rule accepts all ICMP traffic. This protocol is used for many network diagnostics tasks and it's generally a good idea to allow it.

sudo nft add rule inet filter input ip protocol icmp accept

#The fourth rule accepts all ICMPv6 traffic (the equivalent of ICMP for IPv6).

sudo nft add rule inet filter input ip6 nexthdr icmpv6 accept

#The fifth rule accepts all incoming traffic to HTTP (port 80), HTTPS (port 443) and SSH (port 22).

sudo nft add rule inet filter input tcp dport {http, https, ssh} accept

#The final rule drops all other traffic and counts the number of packets dropped.

sudo nft add rule inet filter input counter drop

# Change port to 2222
#Open the SSH configuration file:

sudo nano /etc/ssh/sshd_config

#Change the port 

Port 2222

#Restart the service

sudo service ssh restart

