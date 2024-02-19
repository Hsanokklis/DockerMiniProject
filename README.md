# DockerMiniProject - Personal Finance with Firefly III 

## Overview of Project

**Goals:** Deploy [Firefly III](https://www.firefly-iii.org/) and an Nginx Proxy via Docker

**Description:**
For this project you will need to follow the [Firely III](https://docs.firefly-iii.org/how-to/data-importer/installation/docker/) documentation on how to install their container. Once you have the yaml file for firefly, you will set up a nginx proxy in front of the firefly interface for forward it to port 80 when browsing on your localhost.

**Pre-Requisites:** 
* Installed Docker
* Installed Docker Compose

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
* use `docker stop container_name` to stop a specific container
* use 

## Set up Firefly III Container

**Make a project directory** 

This is where you will place all of your project files and where docker will pull from to start your container. 

## Set up Nginx proxy 
