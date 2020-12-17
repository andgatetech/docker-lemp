# Dockerize LEMP Development Environment
This document provide a guideline for setup and configure complete dockerize LEMP development environment with laravel. Also will provide guideline how to maintain code quality and standard.

### Configuration Specification:
* PHP (version:7.3.5)
* MySQL (version:5.7)
* Nginx (version:latest)
* Laravel (version:8.x)

### Instruction: 
#### Setup and configure docker environment
- Step 1: Install docker. Command: sudo apt install docker
- Step 2: Install docker compose. Command: sudo apt install docker-compose. Ref: https://docs.docker.com/compose/install/
- Step 3: Check docker version. Command: docker --version
- Step 4: Check docker compose version: docker-compose --version
- Step 5: Check list of container to ensure all container is running without error. Command: docker ps

#### Get Project From Github.com:
- Step 1: Install git at local computer. Ref: https://linuxhint.com/install_git_ubuntu_20-24/
- Step 2: Clone project from github. Command: git clone git@github.com:techbeansjp/digram.git
- Step 3: Go to project folder from terminal. Ref Command: cd /var/www/diagram.
- Step 4: Checkout to develop branch. Command git checkout develop

#### Configure and build docker containers:
- Step 1: Go to project folder from terminal. Ref Command: cd /var/www/diaram (location will be your project location).
- Step 2: Create docker env file. command: sudo cp .env.docker.example .env
- Step 3: Update variables value inside .env if need.
- Step 4: Build container. Command: docker-compose build (If docker user group not configured then user sudo. Command: sudo docker-compose build)
- Step 5: Start containers: Command: "docker-compose up" (with console log) or "docker-compose up -d" (run in background without console log)

#### Setup Directory Permission:
- Step 1: run command from terminal. Command: sudo chmod -R 777 storage bootstrap/cache

#### Configure Laravel:
- Step 1: Add and configure laravel environment file. Go to project folder from terminal (cd /digram/var/www/digram) and run command "cp .env.example. .env".
- Step 2: Update .env file if need.
- Step 3: Go to sh (bash) of PHP_FPM container. Command: docker exec -it DIGRAM_PHP_FPM sh
- Step 4: Install composer: composer install
- Step 5: Clear previous cache if have. Command: php artisan cache:clear
- Step 6: Cache configuration: Command: php artisan config:cache 

#### Create Database:
- Step 1: Go to http://localhost:8080 from browser. Login using authentication provided at Database Access Section.
- Step 2: Create new database with name "digram" and user "myuser". Assign newly created user to database "digram"

#### Install and configure Passport::
- Step 7: Get Passport. Command: composer require laravel/passport 
- Step 8: Run database migration. Command: php artisan migrate 
- Step 9: Install passport. Command: php artisan passport:install 

#### Checking Project:
- Step 1: Check site is running witout any error by going to http://localhost from browser.

#### Check PhpMyAdmin:
- Step 1: Check phpmyadmin is working without any error by going to http://localhost:8080 from browser and login. Check database tables if need.

#### Database Access: can be access through two way either using phpmyadmin or sql client 
- host: localhost
- port: 3306
- user: myuser
- password: mypassword
- database: digram 
- root user: root 
- root password: root123!
- PhpMyAdmin Url: http://localhost:8080

###### Note: If any configuration changed at docker config folder or docker-compose.yml file must need to rebuild docker container

### Code Quality Check : PhpMD 
Instruction: This project configured by following workflow to ensure code quality. Ruleset of code quality is pre-defined by ruleset-laravel.xml file. So without complying with defined ruleset code will not be merged with develop or master branch from feature branch.
Before creating any PULL REQUEST must need to check code quality at local machine.
- Command to check code quality: vendor/bin/phpmd app/ ansi ruleset-laravel.xml

### Coding Standard Fixer: php-cs-fixer
Instruction: To fix coding standard developer or engineer must need to run this command locally before push to remote git repository (github.com).
- Command: php artisan fixer:fix --dry-run

### Unit Testing : PhpUnit
Instruction: Without passing unit testing developer or engineer not able to merge any feature branch code to develop or master branch. So, run unit testing at local before push code to remote repository
- Command: vendor/bin/phpunit
