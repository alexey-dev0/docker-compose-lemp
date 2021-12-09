# Docker Compose LEMP stack

All you need to webdev:

* PHP
* Nginx
* MySQL
* phpMyAdmin

Current PHP version is 8.1.x

##  Installation

* Clone this repository on your local computer
* configure .env as needed
* Run the `docker-compose up -d`.

```shell
git clone https://github.com/alexey-dev0/docker-compose-lemp.git
cd docker-compose-lemp/
cp example.env .env
// modify example.env as needed
docker-compose up -d
```

Your LEMP stack is ready. You can access phpinfo() via `http://localhost`.

##  Configuration and Usage

### Configuration
This package comes with default configuration options. You can modify them by creating `.env` file in your root directory.
To make it easy, just copy the content from `example.env` file and update the environment variable values as per your need.

---
#### PHP

**PHP_VERSION**
_Is used to specify which PHP Version you want to use. For now, it's only available version 8.1_

`php.ini` available in `./config/php`

#### Xdebug

**XDEBUG_LOCAL_IP**
_Your local IP for debug connection._

**XDEBUG_SERVER_NAME**
_Your serverName option to IDE server settings._

---
#### Nginx

You can change `nginx.conf` or add you sites configs in `sites` folder in `./config/nginx`.

---
#### Database

**DB_VERSION**
_Define which MySQL version you would like to use. For now, it's only available version 8._

All your MySQL data files will be stored in `./data/mysql`.

MySQL logs stored in `./logs/mysql`.

---
## Web Server

Nginx is configured to run on port 80. So, you can access it via `http://localhost`.

#### Connect via SSH

You can connect to web server using `docker-compose exec` command to perform various operation on it. Use below command to login to container via ssh.

```shell
docker-compose exec php bash
```

## phpMyAdmin

phpMyAdmin is configured to run on port 8080. Use following default credentials.

http://localhost:8080/  
username: root  
password: secret

---
### Thanks to

The creation of this build was inspired by this stack

[sprintcube/docker-compose-lamp]()