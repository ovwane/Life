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

### VHosts

```
vi /etc/nginx/nginx.conf
```

```
include /etc/nginx/vhosts/*;
```

```
sudo mkdir vhsots;
cd vhosts;
touch phpmyadmin.conf;
```

```
server {
	listen 80;
	server_name db.cuiqingcai.com;
	
	index index.php index.html index.htm;
	root /var/www/phpmyadmin;
	
	location / {
		try_files $uri $uri/ =404;
	}
	
	location ~ \.php$ {
	#	fastcgi_pass 127.0.0.1:9000;
	#	# With php5-fpm:
		fastcgi_pass unix:/run/php/php7.0-fpm.sock;
		fastcgi_index index.php;
		fastcgi_param SCRIPT_FILENAME /var/www/phpmyadmin$fastcgi_script_name;
		include fastcgi_params;
		error_log  /var/log/nginx/phpmyadmin.error.log;
	}
}
```

