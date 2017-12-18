# devenv
redmine + gitlab + jenkins

## Description

## Requirement

## Usage

### redmine

#### reference

https://github.com/sameersbn/docker-redmine

#### installing plugins

`cd ./docker/redmine/redmine/plugins  
git clone xxxxx`

if the gem installation fails after adding a new plugin, please retry after removing the ./docker/redmine/redmine/tmp directory.

#### uninstalling plugins

`docker run --name=redmine -it --rm \  
  --volume=./docker/redmine/redmine:/home/redmine/data \  
  sameersbn/redmine:3.4.2 \  
  app:rake redmine:plugins:migrate NAME=plugin_name VERSION=0`

`rm -rf ./docker/redmine/redmine/plugins/plugin_name`

#### installing themes

`cd ./docker/redmine/redmine/themes  
git clone https://github.com/makotokw/redmine-theme-gitmike.git gitmike`

#### uninstalling themes

`rm -rf /srv/docker/redmine/redmine/themes/theme_name`


#### maintenance

##### creating backups

`docker stop redmine && docker rm redmine`

`docker run --name redmine -it --rm [OPTIONS] \  
  sameersbn/redmine:3.4.2 app:backup:create`

`docker exec -it redmine redmine-backup-create`

##### restoring backups

`docker stop redmine && docker rm redmine`

`docker run --name redmine -it --rm [OPTIONS] \  
  sameersbn/redmine:3.4.2 app:backup:restore`

`docker run --name redmine -it --rm [OPTIONS] \  
  sameersbn/redmine:3.4.2 app:backup:restore BACKUP=1417624827_redmine_backup.tar`

#### shell access
docker exec -it mysql bash

### gitlab

#### shell access
docker exec -it gitlab bash

### jenkins

## Install



## Author

Okazaki Masaaaki o.masaaki@me.com
