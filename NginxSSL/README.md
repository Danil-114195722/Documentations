# How to install Nginx on server and up certbot for automatic SSL release

#### (use sudo if you are not root)

## Initial Nginx setup

### 1. Update packages and install nginx package:
```shell
apt update
apt install nginx
```

### 2. Adjusting the Firewall
```shell
ufw app list

# output:

#  Available applications:
#  Nginx Full
#  Nginx HTTP
#  Nginx HTTPS
#  OpenSSH
```

### 3. Use needed setting from list and check status after updates:
```shell
ufw allow 'Nginx Full'
ufw status
```

### 4. If output of `sudo ufw status` is `inactive` enter the next command:
```shell
ufw enable

# output:

# Firewall is active and enabled on system startup
```

### 5. Checking your Web Server
```shell
systemctl status nginx
```

### 6. 