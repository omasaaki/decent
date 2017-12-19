# devenv
redmine + gitlab + jenkins

## Description

## Requirement

## Usage

### redmine

#### reference

https://github.com/sameersbn/docker-redmine

#### installing plugins

    cd ./docker/redmine/redmine/plugins
    git clone xxxxx

if the gem installation fails after adding a new plugin, please retry after removing the ./docker/redmine/redmine/tmp directory.

    docker exec -it devenv_redmine_1 bash
    cd /home/redmine/redmine
    gem install rake
    rake --trace db:migrate RAILS_ENV=production

#### uninstalling plugins

    docker run --name=redmine -it --rm \
    --volume=./docker/redmine/redmine:/home/redmine/data \
    sameersbn/redmine:3.4.2 \
    app:rake redmine:plugins:migrate NAME=plugin_name VERSION=0

    rm -rf ./docker/redmine/redmine/plugins/plugin_name

#### installing themes

    cd ./docker/redmine/redmine/themes
    git clone https://github.com/makotokw/redmine-theme-gitmike.git gitmike

#### uninstalling themes

    rm -rf /srv/docker/redmine/redmine/themes/theme_name


#### maintenance

##### creating backups

    docker stop redmine && docker rm redmine

    docker run --name redmine -it --rm [OPTIONS] \
    sameersbn/redmine:3.4.2 app:backup:create

    docker exec -it redmine redmine-backup-create

##### restoring backups

    docker stop redmine && docker rm redmine

    docker run --name redmine -it --rm [OPTIONS] \
    sameersbn/redmine:3.4.2 app:backup:restore

    docker run --name redmine -it --rm [OPTIONS] \
    sameersbn/redmine:3.4.2 app:backup:restore BACKUP=1417624827_redmine_backup.tar

#### shell access
docker exec -it devenv_redmine_1 bash
docker exec -it devenv_redmine-mysql_1 bash

#### plugins

##### Easy Gantt Plugin

https://www.easyredmine.com/redmine-gantt-plugin

##### Knowledgebase

http://www.redmine.org/plugins/redmine_knowledgebase

    cd ./docker/redmine/redmine/plugins
    git clone https://github.com/alexbevi/redmine_knowledgebase.git

    docker exec -it devenv_redmine_1 bash
    cd /home/redmine/redmine
    ...
    bundle exec rake --trace db:migrate RAILS_ENV=production
    bundle exec rake redmine:plugins:migrate NAME=redmine_knowledgebase

##### Theme Changer

https://www.r-labs.org/projects/themechanger

##### redmine_work_time

https://github.com/tkusukawa/redmine_work_time

    cd ./docker/redmine/redmine/plugins
    git clone https://github.com/tkusukawa/redmine_work_time.git

    docker exec -it devenv_redmine_1 bash
    cd /home/redmine/redmine
    ...
    bundle exec rake --trace db:migrate RAILS_ENV=production

##### absolute_dates

https://github.com/suer/redmine_absolute_dates

    cd ./docker/redmine/redmine/plugins
    git clone https://github.com/suer/redmine_absolute_dates.git

##### checklists

https://www.redmineup.com/pages/plugins/checklists

##### redmine_issue_templates

https://github.com/akiko-pusu/redmine_issue_templates

    cd ./docker/redmine/redmine/plugins
    git clone https://github.com/akiko-pusu/redmine_issue_templates.git

    docker exec -it devenv_redmine_1 bash
    cd /home/redmine/redmine
    ...
    bundle exec rake redmine:plugins:migrate RAILS_ENV=production

##### redmine_xlsx_format_issue_exporter

https://github.com/two-pack/redmine_xlsx_format_issue_exporter

    cd ./docker/redmine/redmine/plugins
    git clone https://github.com/two-pack/redmine_xlsx_format_issue_exporter.git
    ...
    bundle install --without test

#### themes

##### Redmine A1 theme

https://www.redmineup.com/pages/themes/a1

##### Redmine Circle theme

https://www.redmineup.com/pages/themes/circle

##### Minelab

http://hardpixel.github.io/minelab/

##### redmine-theme-gitmike

https://github.com/makotokw/redmine-theme-gitmike

    cd ./docker/redmine/redmine/themes
    git clone https://github.com/makotokw/redmine-theme-gitmike.git

##### redmine-theme-flat

https://github.com/tsi/redmine-theme-flat

    cd ./docker/redmine/redmine/themes
    git clone https://github.com/tsi/redmine-theme-flat.git


### gitlab

#### shell access
docker exec -it devenv_gitlab_1 bash
docker exec -it devenv_gitlab-mysql_1 bash

### jenkins

## Install



## Author

Okazaki Masaaaki o.masaaki@me.com
