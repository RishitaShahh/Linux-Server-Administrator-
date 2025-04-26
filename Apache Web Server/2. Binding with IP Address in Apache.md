

# Configuring Apache for IP Binding and Virtual Hosting

Apache offers the flexibility to bind to specific IP addresses and ports, enabling the hosting of multiple websites on a single server. This guide will walk you through configuring Apache to bind to various IP addresses and setting up Virtual Hosts to manage multiple websites.

## 1. Apache Binding Overview
Apache allows binding to:

- A specific IP address
- All available IP addresses
- Multiple ports

---

## 1.1 Binding Apache to All IP Addresses
By default, Apache listens to all available IP addresses:

```bash
Listen 80
```

### Update Apache Configuration
Search for the `Listen` directive in the configuration file:
```bash
#Listen 12.34.56.78:80
Listen 80
```
Apache listens on port *80* across all available network interfaces.

### Restart Apache for Changes to Take Effect
```bash
systemctl restart httpd.service
```

#### Example output from *netstat*:
```bash
netstat -nltup | grep httpd
```

#### Output:
```bash
tcp      0         0.0.0.0:80      0.0.0.0:*      LISTEN      1234/httpd
```
Here, `0.0.0.0` shows that Apache is listening on all IP addresses.

---

## 1.2 Binding Apache to a Specific IP Address
To restrict Apache to a particular IP address:

### Step 1: Open the Apache Configuration File
```bash
vim /etc/httpd/conf/httpd.conf
```

### Step 2: Modify the `Listen` Directive
```bash
Listen 127.0.0.1:80
```

### Update Apache Configuration
Locate the `Listen` section:
```bash
#Listen 12.34.56.78:80
Listen 127.0.0.1:80
```
This will bind Apache to the `127.0.0.1` (localhost).

### Restart Apache After Modifying
```bash
systemctl restart httpd.service
```

#### Example output from *netstat*:
```bash
netstat -nltup | grep httpd
```

#### Output:
```bash
tcp      0      0  127.0.0.1:80      0.0.0.0:*      LISTEN      1234/httpd
```

---

## 1.3 Binding Apache to a Local Network IP
To bind Apache to a specific LAN IP address, such as *192.168.112.145*:

### Step 1: Open the Apache Configuration File
```bash
vim /etc/httpd/conf/httpd.conf
```

### Step 2: Modify the `Listen` Directive
```bash
Listen 192.168.112.145:80
```

### Update Apache Configuration
Search for the `Listen` directive:
```bash
#Listen 12.34.56.78:80
Listen 192.168.112.145:80
```

### Restart Apache After Modifying
```bash
systemctl restart httpd.service
```

#### Example output from *netstat*:
```bash
netstat -nltup | grep httpd
```

#### Output:
```bash
tcp      0      0  192.168.112.145:80      0.0.0.0:*      LISTEN      1234/httpd
```

---

## 1.4 Configuring Apache to Listen on Multiple Ports
Apache can listen on multiple ports simultaneously for different websites:

### Step 1: Open the Apache Configuration File
```bash
vim /etc/httpd/conf/httpd.conf
```

### Step 2: Add Additional Ports
```bash
firewall-cmd --permanent --add-port=81/tcp
firewall-cmd --permanent --add-port=82/tcp
firewall-cmd --reload
```

### Step 3: Add Multiple `Listen` Directives
```bash
Listen 80
Listen 81
Listen 82
```

### Restart Apache After Changes
```bash
systemctl restart httpd.service
```

#### Example output from *netstat*:
```bash
netstat -nltup | grep httpd
```

#### Output:
```bash
tcp      0      0  0.0.0.0:80      0.0.0.0:*      LISTEN      1234/httpd
tcp      0      0  0.0.0.0:81      0.0.0.0:*      LISTEN      1234/httpd
tcp      0      0  0.0.0.0:82      0.0.0.0:*      LISTEN      1234/httpd
```

---

## 2. Restart Apache After Configurations
Once the configuration is updated, restart Apache:
```bash
systemctl restart httpd.service
```

### Check for Configuration Syntax Errors:
```bash
httpd -t
```

---

## 3. Verify Apache Binding
Use *netstat* to confirm that Apache is listening on the correct IP addresses and ports:
```bash
netstat -nltup | grep httpd
```

---

## Summary of Apache Binding

| Binding Type         | Example Configuration              | Use Case                                  |
|----------------------|-----------------------------------|-------------------------------------------|
| Bind to All IPs      | Listen 80                         | Default, accessible from all interfaces  |
| Bind to Specific IP  | Listen 127.0.0.1:80               | Restrict to localhost or specific IP    |
| Bind to LAN IP       | Listen 192.168.112.145:80         | Restrict to LAN IP only                 |
| Bind to Multiple Ports | Listen 80, Listen 81, Listen 82   | Enable Apache to listen on multiple ports|

---

# Virtual Hosting with Apache

## 1. Set Up Website Directories

1. Navigate to the web root:
   ```bash
   cd /var/www/html/
   ```

2. Create directories for each site:
   ```bash
   mkdir site1 site2 site3
   ```

3. Adjust permissions:
   ```bash
   chown -Rv apache:apache site1 site2 site3
   ```

4. Download a website template:
   ```bash
   wget "https://www.free-css.com/assets/files/free-css-templates/download/page296/oxer.zip"
   ```

5. Extract the template:
   ```bash
   unzip templatemo_571_hexashop.zip
   ```

6. Remove the ZIP file:
   ```bash
   rm -rf templatemo_571_hexashop.zip
   ```

7. Move the extracted files:
   ```bash
   mv -v templatemo_571_hexashop /var/www/html/site1/
   ```

8. Test the site by accessing it via:
   ```bash
   192.168.112.145/site1/
   ```

## 2. Configure Virtual Hosts

Edit the Apache main configuration file:
```bash
vim /etc/httpd/conf/httpd.conf
```
Ensure the following line is included:
```apache
IncludeOptional conf.d/*.conf
```

Add virtual hosts for each website:
```apache
<VirtualHost 192.168.112.145:80>
    DocumentRoot /var/www/html/site1/
    DirectoryIndex index.html
</VirtualHost>

<VirtualHost 192.168.112.146:80>
    DocumentRoot /var/www/html/site2/
    DirectoryIndex index.html
</VirtualHost>

<VirtualHost 192.168.112.147:80>
    DocumentRoot /var/www/html/site3/
    DirectoryIndex index.html
</VirtualHost>
```

Restart Apache to apply the changes:
```bash
systemctl restart httpd.service
```

---

## 3. Create Individual Virtual Host Files

Create separate virtual host configuration files under `/etc/httpd/conf.d/`.

### For Site 1:
```bash
vim /etc/httpd/conf.d/site1.conf
```
Example:
```apache
<VirtualHost 192.168.112.145:80>
    DocumentRoot /var/www/html/site1/
    DirectoryIndex index.html
</VirtualHost>
```

### For Site 2:
```bash
vim /etc/httpd/conf.d/site2.conf
```
Example:
```apache
<VirtualHost 192.168.112.146:80>
    DocumentRoot /var/www/html/site2/
    DirectoryIndex index.html
</VirtualHost>
```

### For Site 3:
```bash
vim /etc/httpd/conf.d/site3.conf
```
Example:
```apache
<VirtualHost 192.168.112.147:80>
    DocumentRoot /var/www/html/site3/
    DirectoryIndex index.html
</VirtualHost>
```

### Restart Apache:
```bash
systemctl restart httpd.service
```

---

## 4. Validate the Configuration

Check if Apache configuration is correct:
```bash
httpd -t
```

---

## 5. Test Apache Setup

Confirm that Apache is listening on the correct ports:
```bash
netstat -nltup | grep httpd
```

---

## Summary of Virtual Hosting

| Binding Type           | Example Configuration               | Use Case                                    |
|------------------------|-------------------------------------|---------------------------------------------|
| Bind to All IPs        | `<VirtualHost *:80>`                | Use when hosting multiple websites on all interfaces |
| Bind to Specific IP    | `<VirtualHost 192.168.112.145:80>`  | Configure Apache to host sites on specific IPs |
| Multiple IP Bindings   | Multiple `<VirtualHost>` blocks     | Use to manage several virtual hosts on distinct IPs |

This guide will assist you in configuring Apache with specific IP bindings and virtual hosting setups, ensuring smooth management of multiple websites on a single server.

---
