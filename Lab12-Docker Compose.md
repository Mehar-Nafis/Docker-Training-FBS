## Docker Compose 

If Docker Compose is not integrated with your current Docker Engine version, you can install it using the commands below:

```bash
sudo apt update
sudo apt install docker-compose
```
Create a directory
```
mkdir compose && cd compose
```
Create and open the docker-compose.yaml file
```
vi docker-compose.yaml
```
Add the following content to the file
```
version: '3.3'

services:
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: somewordpress
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress

  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - "80:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
volumes:
  db_data: {}
```
Start the services in detached mode
```
docker-compose up -d
```
Check the status of the containers
```
docker-compose ps
```
View all running containers
```
docker container ls
```
List Docker networks
```
docker network ls
```
List Docker volumes
```
docker volume ls
```
To stop and remove all containers, networks, and volumes created
```
docker-compose down
```
