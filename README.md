# Dockerize LEMP Development Environment
Complete Dockerize LEMP development environment.

Instruction: How add multiple site

Add site:
- Create new folder {your application folder name} inside public_html
- Copy default.conf as {your application folder name}.conf
- Edit root   /public_html/website; to root   /public_html/{your application folder name};
- rebuild docker containers using command: docker-compose build

Access database:

Database can be access through two way either using phpmyadmin or sqlclient by using access details provided below-
- MYSQL_ROOT_HOST: '%'
- MYSQL_ROOT_PASSWORD: myroot
- MYSQL_DATABASE: mydatabase
- MYSQL_USER: myuser
- MYSQL_PASSWORD: mypassword
