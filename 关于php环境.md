## Ubuntu搭建Nginx+PHP7+MySQL

### MySQL

```
sudo apt-get -y install mysql-server mysql-client
```

### Nginx

```
sudo apt-get -y nginx
```

### PHP7

```
sudo apt-add-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get -y install php7.0 php7.0-cli php7.0-fpm php7.0-gd php7.0-json php7.0-mysql php7.0-readline
```

### PHPMyAdmin

```
sudo apt-get -y install phpmyadmin
sudo ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin
```

