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

Copy/paste the yml files from the [Firely website]([url](https://docs.firefly-iii.org/how-to/data-importer/installation/docker/)) or the project files in this project

* `nano` [docker.compose.yml](docker-compose.yml)
* `nano` [.importer.env](.importer.env)
* `nano` [.db.env](.db.env)
* `nano` [.env](.env)




## Set up Nginx proxy 
