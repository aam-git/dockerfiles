Opencart 3.0.3.1, Apache 2, PHP7.2-fpm, Mysql 8
========

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

[1]: http://www.opencart.com/index.php
