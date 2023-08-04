## Description and Table of Contents

In this GitHub repository, you will find the code and instructions for setting up a web server with Apache, MySQL, PHP, and additional security configurations. The steps are structured and organized below.

### Table of Contents
1. [User Creation](#user-creation)
2. [System Updates and Package Installations](#system-updates-and-package-installations)
3. [MySQL Configuration](#mysql-configuration)
4. [Apache Configuration](#apache-configuration)
5. [Firewall (UFW) Configuration](#firewall-ufw-configuration)
6. [Fail2ban Installation and Configuration](#fail2ban-installation-and-configuration)
7. [Additional Network Configuration](#additional-network-configuration)
8. [Change SSH Port](#change-ssh-port)

## User Creation
### Creation of Usernames
- Create usernames for each user using the following commands:

```bash
adduser amin
adduser maikl
```

## System Updates and Package Installations
### Updating the System
- Update the repository with the commands:

```bash
apt update
apt upgrade
```

### Installing Apache
- Install Apache with the command:

```bash
apt-get install apache2
```
- Install MySQL with the command:

```bash
apt-get install mysql-server
```
- Install PHP with the command:

```bash
apt-get install php
```
## MySQL Configuration
- Create a MySQL database and user:

```sql
CREATE DATABASE wikidb;
CREATE USER 'new_mysql_user'@'localhost' IDENTIFIED BY 'PASSWORD';
GRANT ALL ON wikidb.* TO 'new_mysql_user'@'localhost';
```

## Apache Configuration
- Navigate to the Apache configuration directory (usually located at /etc/apache2/sites-available/):

```bash
sudo nano /etc/apache2/sites-available/wiki.conf
```

- Disable the default Apache site and enable the wiki.conf configuration:

```bash
sudo a2dissite 000-default.conf
sudo a2ensite wiki.conf
sudo service apache2 restart
```

- Enable the SSL module to resolve the "Invalid command 'SSLEngine'" error:

```bash
sudo a2enmod ssl
sudo service apache2 restart
```

## Firewall (UFW) Configuration
- Check if UFW (Uncomplicated Firewall) is installed:

```bash
sudo ufw status
```

- Install UFW if not already installed:

```bash
sudo apt-get install ufw
```

- Configure the firewall to allow SSH and HTTPS connections:

```bash
sudo ufw default deny incoming
sudo ufw allow ssh
sudo ufw allow https
sudo ufw enable
sudo ufw status
```

## Fail2ban Installation and Configuration
- Install Fail2ban:

```bash
sudo apt install fail2ban
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

- Create a local configuration file for Fail2ban:

```bash
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
sudo nano /etc/fail2ban/jail.local
```

- Add the following custom configuration to the `jail.local` file:

```ini
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
```

## Additional Network Configuration
- Configure additional network rules using NFT (nftables):

```bash
sudo nft add table inet filter
sudo nft add chain inet filter input { type filter hook input priority 0 \; }
sudo nft add rule inet filter input ct state established,related accept
sudo nft add rule inet filter input iifname lo accept
sudo nft add rule inet filter input ip protocol icmp accept
sudo nft add rule inet filter input ip6 nexthdr icmpv6 accept
sudo nft add rule inet filter input tcp dport {http, https, ssh} accept
sudo nft add rule inet filter input counter drop
```

## Change SSH Port
- Open the SSH configuration file:

```bash
sudo nano /etc/ssh/sshd_config
```

- Change the port number to 2222:

```
Port 2222
```

- Restart the SSH service:

```bash
sudo service ssh restart
```


