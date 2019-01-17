Opencart 3.0.3.1
========
powered by Apache 2, PHP7.2-fpm, MySQL 8.0.13 and Mcrypt 1.0.2


[OpenCart][1] is designed feature rich, easy to use, search engine
friendly and with a visually appealing interface.

## docker-compose.yml

```yaml
version: '2'
services:
  mysql:
    image: mysql:8.0
    environment:
      - MYSQL_DATABASE=opencart
      - MYSQL_ROOT_PASSWORD=change_to_secure_password
    volumes:
      - mysql_data:/var/lib/mysql
  opencart:
    image: aamservices/opencart
    ports:
      - '80:80'
      - '443:443'
    volumes:
      - opencart_data:/var/www/html
    depends_on:
      - mysql
volumes:
  mysql_data:
    driver: local
  opencart_data:
    driver: local
```

Instructions for Composer
========

```
1) create docker-compose.yml from content above, make sure to use a secure mysql root password
2) docker-compose up -d
3) go to your web url (eg. http://127.0.0.1)
4) go through the opencart standard install procedure
 - DB Driver is "MySQLi"
 - Hostname is "mysql"
 - Username is "root"
 - Password is "secure_password_here" (though you should have changed this)
 - Database is "opencart"
 - Enter your own details for step 2
5) Opencart Install should now be complete, you can now delete the install folder, and start using opencart.
```

Please note this is not fully tested yet, so please make sure to fully test everything before taking it into a production environment.

I'll be updating it over the coming weeks if needs be.

[1]: http://www.opencart.com/index.php
