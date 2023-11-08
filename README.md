# Docker-compose.yml

version: '3'
services:
django:
tty: true
build:
context: . # The context is the current directory where the Dockerfile is located
dockerfile: Dockerfile
ports:
- "8000:8000"
depends_on:
- db
volumes:
- django_data:/usr/local
db:
image: mariadb
restart: always
volumes:
- mariadb_data:/var/lib/mysql
environment:
MYSQL_ROOT_PASSWORD: root
MYSQL_USER: admin
MYSQL_PASSWORD: test
MYSQL_DATABASE: database
ports:
- "8889:3306"
volumes:
django_data:
mariadb_data:

