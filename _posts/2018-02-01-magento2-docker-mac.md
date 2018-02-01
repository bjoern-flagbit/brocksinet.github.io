---
layout: post
title: FAST Docker development environment with Magento2 on MacBook with High Sierra
description: Improve your development speed by a good docker setup for magento2!
---
For a long time i was really really really very frustrated because of Docker, Magento2 and High Sierra.
If you search for that you will find a lot of tutorials how to speed up your development environment. 
At the beginning the page load sometimes was over 1 minute, also when you know what to do this is a really
long time to wait for a short test. Later after some Docker updates the waiting time get's down to 20-30 seconds
for one page load. And **now** i have page load times between 2 and 3 seconds on a single frontend page without
layout, block and fpc cache. With that i can focus on development!

### And here is, how you can get this too

**System requirements**
* You are working on a mac with high sierra
* Check that your volume is running on APFS (the new apple file-format)
* You should have at least [docker](hhttps://store.docker.com/editions/community/docker-ce-desktop-mac) stable *Version 17.12.0-ce-mac49 (21995)*
* Check that you have [docker-compose](https://docs.docker.com/compose/install/) also installed
* You should have [docker-sync](http://docker-sync.io/) installed

**Docker configuration**
* Open Docker -> Preferences...
* Open Tab "File Sharing"
    * Check that there is only one folder with all your projects, remove all others like tmp etc. 
    (so docker only search here for file changes)
* Open Tab "Disk"
    * Check that the disk image location is ending with **Docker.raw**
        * If not you have to reset docker to factory defaults 
        (this will drop/delete your containers)
* Open Tab "Advanced"
    * Set **CPUs to 4**
    * Set Memory at least to **8 GB**
* Apply all the changes and check after restart if they are set correct

**Check your storage driver**

put this in a terminal:
    
    docker info | grep "Storage Driver"

it should output this: 

    Storage Driver: overlay2

#### Project configuration with docker-sync and docker-compose

Our project folder structure looks like this:

![Docker Example Magento2 Project Folder Structure](https://raw.githubusercontent.com/bjoern-flagbit/brocksinet.github.io/afce34c161d4574b59cb21eecdfd3fa1ddb58787/images/_posts/docker/project-folder-structure.png "Docker Example Magento2 Project Folder Structure")

Add the docker-sync.yml and docker-compose.mac.yml to your project folder (examples see below)

Start docker-sync first (you should be in the project folder, where your docker-sync.yml is)

    docker-sync start
    	
Start your docker containers with docker-compose

    docker-compose -f docker-compose.mac.yml up -d 
    	
**Example docker-sync.yml**

	version: "2"
    
    options:
      verbose: true
      compose-file-path: 'docker-compose.mac.yml'
      unison_image: 'eugenmayer/unison'
      cli_mode: 'auto'
      max_attempt: 3000
    
    syncs:
      php-projectname-sync:
        notify_terminal: true
        src: './src'
        sync_strategy: 'unison'
        sync_excludes: [
          'Path .git',
          'Name .gitignore',
          'BelowPath node_modules',
          'BelowPath bower_components',
          'BelowPath sass-cache',
          'BelowPath .sass-cache',
          'Path var/cache',
          'Path var/page_cache',
          'Path var/session',
          'BelowPath .DS_Store'
        ]
        sync_userid: '1000'
        max_attempt: 10
    
      mysql-projectname-sync:
        notify_terminal: true
        src: './.docker/mysql/config/'
        sync_strategy: 'unison'
        sync_prefer: 'src'
        watch_in_container: true
	
**Example docker-compose.mac.yml**

	version: "2"
    
    services:
    
      nginx-projectname:
        build: "./.docker/nginx-ubuntu/"
        container_name: "nginx-projectname"
        volumes_from:
          - php-projectname
        restart: unless-stopped
        ports:
          - "8080:8080"
        expose:
          - "9000"
          - "8080"
        networks:
          - projectname-net
    
      mysql-projectname:
        image: mysql:5.6
        container_name: "mysql-projectname"
        volumes:
          - mysql-projectname-sync:/etc/mysql/conf.d
        environment:
          MYSQL_ROOT_PASSWORD: "root"
          MYSQL_DATABASE: "projectname_dev"
        ports:
          - "3306:3306"
        expose:
          - "3306"
        networks:
          - projectname-net
    
      php-projectname:
        build: "./.docker/php-ubuntu/"
        container_name: "php-projectname"
        environment:
          XDEBUG_CONFIG: "remote_host=docker.for.mac.localhost"
          PHP_XDEBUG_ENABLED: 1
          PHP_IDE_CONFIG: "serverName=projectname"
        depends_on:
          - mysql-projectname
          - redis-projectname
        volumes:
          - php-projectname-sync:/var/www/html:nocopy,delegated
        networks:
          - projectname-net
    
      mailcatcher-projectname:
        image: tophfr/mailcatcher
        container_name: "mailcatcher-projectname"
        ports:
          - "1080:80"
          - "1025:25"
        networks:
          - projectname-net
    
      redis-projectname:
        image: redis
        container_name: "redis-projectname"
        ports:
          - "6379:6379"
          - "6380:6380"
        expose:
          - "6379"
        networks:
          - projectname-net
    
      varnish-projectname:
        restart: unless-stopped
        build: ./.docker/varnish
        container_name: "varnish-projectname"
        ports:
          - "6081:6081"
          - "6082:6082"
        depends_on:
          - nginx-projectname
        expose:
          - "6081"
          - "6082"
        networks:
          - projectname-net
    
      sslterm-projectname:
        build: "./.docker/ssl-term/"
        container_name: "sslterm-projectname"
        depends_on:
          - varnish-projectname
        restart: unless-stopped
        ports:
          - "80:80"
          - "443:443"
        networks:
          - projectname-net
    
    networks:
      projectname-net:
        driver: bridge
    
    volumes:
      php-projectname-sync:
        external: true
      mysql-projectname-sync:
        external: true

### Now open the page in your browser and enjoy the speed!

#### Links to additional resources
* [Performance tuning for volume mounts](https://docs.docker.com/docker-for-mac/osxfs-caching/)
