## Description
Docker development environment for Symfony 4 applications. 

## Features
* Nginx
* PHP 7.2
* PostgreSQL
* Adminer
* Elasticsearch 6.1.1 with Kibana

## Requirements
### Supported Docker and Docker-Compose versions
docker-engine >=1.13.0  
docker-compose >=1.10.0

## Usage
#### Installation
1. `git clone https://github.com/karmrt/Symfony4-Docker.git symfony4_app`
2. `cd symfony4_app`
3. `docker-compose up -d`
4. `docker-compose exec php-fpm composer create-project symfony/skeleton`
5. `mv symfony/* .; rmdir symfony`

#### Accessing your project 
Webserver: http://localhost  
Kibana: http://localhost:5601  
Elasticsearch: http://localhost:9200  
Adminer: http://localhost:8080  
* PostgreSQL user: admin
* PostgreSQL password: admin

#### Working with docker
Launch containers:  
`docker-compose up -d`  
Destroy containers:  
`docker-compose down`  
Stop containers:  
`docker-compose kill`  
Execute command inside a container:  
`docker-compose exec [container-name] [command]`  
Go inside a container:  
`docker-compose exec [container-name] bash`
