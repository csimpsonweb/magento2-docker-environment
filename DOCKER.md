# Using Magento inside Docker

## Initializing the instance

In the project root directory run `bin/setup` to initialise the project and start docker. You will be put through an
interactive setup script which explains each step. At the end you will be given the URL to access the site from.

If you are doing frontend asset compilation (less, js) etc. Run `bin/setup-frontend` to run the required scripts to
setup compilation in the container. Once completed you can run `bin/grunt watch` and the primary theme will be generated
as expected on file updates.

## Built in Commands

To ease the usage process for non docker users, a set of scripts have been provided to run certain tasks from the host.
1. `bin/bash` drop a shell into the fpm container
2. `bin/permissions` set file permissions back to required defaults
3. `bin/restart` restart the docker containers
4. `bin/setup` initial setup for site
5. `bin/setup-frontend` initial frontend setup for site
6. `bin/start` start the docker containers
7. `bin/stop` stop the docker containers

## Access containers

FPM: `docker exec --user=www-data -it attwoolls-outdoors_fpm_1 bash`
DB: `docker exec -it attwoolls-outdoors_db_1 bash`
Nginx: `docker exec -it attwoolls-outdoors_web_1 bash`

To view the logs `docker-compose logs -f`

## Cleanup

To remove the data and everything `docker-compose down -v`

## Common tasks

**Installing a module with composer**

Run `bin/composer require --dev magento/magento-coding-standard`


## Troubleshooting

**Frontend assets not updating on browser refresh**
Make sure you disable magento caching full page cache with `bin/magento cache:disable full_page block_html layout config`