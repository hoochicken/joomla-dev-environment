# Joomla! Development Environment

This repository generated a development environment for the CMS Joomla! It's based on docker. 

There is an xdebuggable container for the Joomla! application. The database is accessable via the phpmyadmin container. And there also is a mail container, that allows you to have a fullgrown e-mail sandbox.

Enjoy :-)

## Docker containers

* traefik
  * available on <http://127.0.0.1:8080> 
  * for routing, so you can access your project e. g. on yourproject.localhost
* mailhog
  * available on <http://mail.localhost>
  * catches all emails send
* phpmyadmin
  * available on <http://sql.localhost>
  * administration of database 
* your project
  * available on PHP 7.4 <http://yourproject74.localhost>
  * available on PHP 8.0 <http://yourproject80.localhost>
  * available on PHP 8.1 <http://yourproject81.localhost>
  * your Joomla! project
  * apache with xdebug

## Requirements

* Docker environment (Docker desktop ...) 

## Usage

~~~shell
# clone repository, e. g. by sheer download or via 
git clone git@github.com:hoochicken/joomla-dev-environment.git

# move to your project
# this will be the root folder
cd yourproject

# start environment
docker-compose up
~~~

* Go to <http://yourproject.localhost>
* Install your joomla
* Database settings
  * database server host name: `mariadb`
  * user name: `root`
  * password: `root`
  * database name: `yourproject` (<= whatever is set in `.env` > DATABASE_NAME)

## Changing Php Version

As you can see in the Dockerfile: the base image is an apache 8.0. If you need another Version, just switch here to apache 8.1 or even back to 7.4.

## Debugger

You can use the common debugger in phpstorm to debug your project:-)

## Recommended step

Adjusting the following two settings lets you use this project setup multiple times without interference.

* `.env`: 
  * rename DATABASE_NAME to something unique, like you website's name
  * e. g. your `yourproject` to `miller`
  * please just small letters or cyphers, no special chats or underscores oder capital letters etc.
* `docker-compose.yml`
  * adjust traefik routes of the service `yourproject` for your project
  * e. g. your `yourproject.localhost` to `miller.localhost` 
  * please just small letters or cyphers, no special chats or underscores oder capital letters etc.
