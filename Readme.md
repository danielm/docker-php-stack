# Docker & PHP 8 boilerplate

Clone me and build cool stuff. This sets up some minimal containers to build PHP API/services.

**Note:** At the moment this is only designed to work during development, and shoun't be used *as is* for production. 
But it can be used as an starting point.

## Install
- Clone the repository
- Create *.env* file from .env.default example
- Add 'my_project.docker' to /etc/hosts files
- docker-compose build && docker-compose up
- Service available at: http://my_project.docker:80/

## Now you got:

- Postgres, Php-FPM and Nginx official images (Alpine)
- Composer also from it's official image.
-  **.env** File to setup Host port mapping, app environment vars, db settings
- Persistent logs and database data for development
- Symfony CLI
- Extra PHP extensions enabled: pdo_pgsql opcache
- Xdebug enabled (debug mode) w/VSCode launch config and ready to go.

## Directories & Files

- .docker/ *Docker building stuff*
- api/ *Whee codes goes*
- var/logs/nginx/ *Nginx logs*
- var/postgres/ *Postgress persistent data*

## ToDo
- Xdebug env vars
- Opcache env vars
- Cleanup / organize ini/entrypoints
- Production build scripts
- Document Env vars
- Review user permissions of persistent data / logs / composer's vendor and any file created from our container
- Cronjobs
- Supervisor
- Laravel cli and its requirements

## About
By [Daniel Morales](https://daniel.uy)
License: Released under the  [MIT license](https://github.com/danielm/uploader/blob/master/LICENSE.txt)
