# start with docker-compose

__docker-compose.yml__

```
server:
  image: rancher/server:v1.4.1
  restart: unless-stopped
  ports:
    - "8080:8080"
  command: --db-host mysql --db-port 3306 --db-user cattle --db-pass cattle --db-name cattle
  links:
    - mysql:mysql

mysql:
  image: mysql
  restart: unless-stopped
  environment:
    - MYSQL_RANDOM_ROOT_PASSWORD=yes
    - MYSQL_DATABASE=cattle
    - MYSQL_USER=cattle
    - MYSQL_PASSWORD=cattle
```
