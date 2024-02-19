# DockerMiniProject - Personal Finance with Firefly III 

## Overview of Project

**Goals:** Deploy [Firefly III](https://www.firefly-iii.org/) and an Nginx Proxy via Docker

**Description:**
For this project you will need to follow the [Firely III](https://docs.firefly-iii.org/how-to/data-importer/installation/docker/) documentation on how to install their container. Once you have the yaml file for firefly, you will set up a nginx proxy in front of the firefly interface for forward it to port 80 when browsing on your localhost.

**Pre-Requisites:** 
* Docker is Installed
    * follow step 1 [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
    * run `docker run hello world` to make sure docker and docker compose is running 


### File structure

**DockerProject**
* [docker-compose.yml](docker-compose.yml)
* .env
* .db.env
* .importer.env
* **nginx**
   * DockerFile
   * nginx.conf
 
  ![image](https://github.com/Hsanokklis/DockerMiniProject/assets/113212665/4004fe7b-9267-491f-8f5c-92b646a7ca55)

### Helpful Tips and Commands

* Copy and paste the YML files directly from the yml Firefly website (yml configurations are super picky!)
* make sure you are in the correct directory when running `docker-compose up -d`
* If a Docker command dosen't work try running it with `sudo`
* use `docker-compose down` to shut down your containers BEFORE making changes to the docker-compose.yml file
* use `docker ps` to view what containers are running
* use `docker ps --all` to view containers that failed
* use `docker stop container_name` to stop a specific container
* use `docker compose build --no-cache` to rebuild containers from scratch
* Use `exec` to execute commands within your container and not your localhost
* When configuring the Firely files, make sure every file except docker-compose.yml has a preceeding period. 

## Set up Firefly III Container

### Make a project directory 

* `mkdir DockerProject`

  _This is where you will place all of your project files and where docker will pull from to start your container_

### Create Firefly YAML files

Use your favorite text editor and creae the files below in the `DockerProject` directory. Copy/paste the yml files from the [Firely website](https://docs.firefly-iii.org/how-to/data-importer/installation/docker/) or the project files in this project.

* [docker.compose.yml](docker-compose.yml)
* [.importer.env](.importer.env)
* [.db.env](.db.env)
* [.env](.env)
  
**If you save all example files and change nothing, it will NOT YET work. You must do a few things:**

* Change `DB_PASSWORD` in `.env` to something else 
* Change `MYSQL_PASSWORD` in `.db.env` to the **SAME** value
* Change `FIREFLY_III_URL` in `.importer.env` to `http://app:8080`
* Change `VANITY_URL` in `.importer.env` to `http://localhost`

## Set up Nginx proxy 

Within the DockerProject directory, make a new directory called `nginx`. You will need to put some config files that the main docker-compose.yml file will pull from to set up the nginx container

* `mkdir nginx`

Within your nginx directory make two files (you can use [this link](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/Docker-Nginx-reverse-proxy-setup-example) or my project files): 
* [Dockerfile](Dockerfile)
* [nginx.conf](nginx.conf)

_Make sure that `proxy_pass` in `nginx.conf` is set to `http://app:8080;`_

## Edit your docker-compose.yml to add the nginx service 

My `docker-compose.yml` project file already has this part in it, so if you copied mine when you created the firely files, then you don't need to do this step. If not, update the `docker-compose.yml` file with the syntax below. 

````
#this goes under the importer section of the file
nginx:
    build: ./nginx
    ports:
      - '80:80'
    links:
      - app
    networks:
      - firefly_iii
````

## Start your Containers! 

* run `sudo docker-compose up -d` 
* run `sudo docker ps` to check that your containers are all running 

If all your files match what I have, and you have changed the configurations to reflect your system, then you should be able to browse to Firely on your browser via `http://localhost`. 

You also shouldn't have to specifiy a port when browsing since nginx will change your request to the default port of 80! 

![image](https://github.com/Hsanokklis/DockerMiniProject/assets/113212665/b5172e0a-98b2-48ad-a130-492f87865882)





