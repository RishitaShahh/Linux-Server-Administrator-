


# Apache Web Server Setup and Configuration

Apache is an open-source web server managed by the **Apache Software Foundation**. It is widely used for hosting websites and web applications because it is flexible, reliable, and easy to configure.

---

## Key Features

- Cross-platform support (Linux, Windows, macOS, and more)
- Modular design (supports modules like `mod_ssl`, `mod_rewrite`)
- Virtual hosting to serve multiple websites
- Security features like SSL/TLS, authentication, and access control
- Customizable using `.htaccess` and `httpd.conf`
- Compatible with server-side languages like PHP, Python, Perl

---

## Common Use Cases

- Hosting static and dynamic websites
- Running CMS platforms like WordPress, Joomla, Drupal
- Acting as a reverse proxy or load balancer
- Providing secure HTTPS communication

---

# Installation and Setup

## 1. Check if Apache is Installed
```bash
rpm -qa | grep httpd
```

## 2. Install Apache
```bash
yum install httpd
```
(Optional) Install all Apache-related packages:
```bash
yum install httpd*
```

## 3. Verify Installation
Check package information:
```bash
rpm -qi httpd
```
List installed files:
```bash
rpm -ql httpd
```
List configuration files:
```bash
rpm -qc httpd
```
List documentation files:
```bash
rpm -qd httpd
```

---

# Configuration

## View Apache Configuration
```bash
cat /etc/httpd/conf/httpd.conf
```
Find module and directory configurations:
```bash
grep conf.modules.d /etc/httpd/conf/httpd.conf
grep conf.d /etc/httpd/conf/httpd.conf
```

---

# Managing Apache Service

## Check Service Status
```bash
systemctl status httpd.service
```

## Start Apache Service
```bash
systemctl start httpd.service
```

## Enable Apache to Start on Boot
```bash
systemctl enable httpd.service
```

## Restart Apache Service
```bash
systemctl restart httpd.service
```

---

# Network and Port Verification

## Check Open Ports
```bash
netstat -nltup
```

Check if port 80 is open:
```bash
netstat -nltup | grep 80
```

Check if Apache is listening:
```bash
netstat -nttup | grep httpd
```

---

# Firewall Configuration (Firewalld)

## Check Firewalld Status
```bash
systemctl status firewalld
```

## Start and Enable Firewalld
```bash
systemctl start firewalld
systemctl enable firewalld
```

## List Firewall Rules
```bash
firewall-cmd --list-all
firewall-cmd --list-services
firewall-cmd --list-ports
```

## Allow HTTP and HTTPS Services
```bash
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
firewall-cmd --reload
```

## Open Specific Ports (Optional)
```bash
firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --permanent --add-port=443/tcp
firewall-cmd --reload
```

## Remove Services or Ports (Optional)
```bash
firewall-cmd --permanent --remove-service=http
firewall-cmd --permanent --remove-service=https
firewall-cmd --reload
```

---

# Apache Process and User Management

## Check Running Processes
```bash
ps -aux | grep httpd
```

## Find Apache User and Group
```bash
cat /etc/passwd | grep apache
cat /etc/group | grep apache
```

---

# Configure Website Files

## Navigate to the Document Root
```bash
cd /var/www/html
```

## Create or Edit index.html
```bash
vim index.html
```

## Remove Existing File (Optional)
```bash
rm -f index.html
```

## Set Ownership of Files
```bash
chown -Rv apache:apache /var/www/html/*
```

---

# Load CSS and Templates

## Download Template
```bash
wget "https://www.free-css.com/assets/files/free-css-templates/download/page296/oxer.zip"
```

## Extract Files
```bash
unzip oxer.zip
rm -f oxer.zip
mv oxer /var/www/html/
```

## Allow Apache to Load CSS Files

Edit the Apache configuration file:
```bash
vim /etc/httpd/conf/httpd.conf
```
Add these lines at the end:
```bash
AddType text/html .shtml
AddType text/css .css
AddOutputFilter INCLUDES .shtml
```

Restart Apache:
```bash
systemctl restart httpd.service
```

Reset ownership:
```bash
chown -Rv apache:apache /var/www/html/*
```

---

# Testing Apache Server

## Create a Test File
```bash
echo 'Test123' > /var/www/html/test.html
```

## Test Apache with curl
```bash
curl http://localhost
```

---
