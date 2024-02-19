# DockerMiniProject - Personal Finance with Firefly III 

## Overview of Project

**Goals:** Deploy [Firefly III](https://www.firefly-iii.org/) and an Nginx Proxy via Docker

**Description:**
For this project you will need to follow the Firely III documentation on how to install their container which can be found here. Once you have the yaml file for firefly, you will set up a nginx proxy in front of the firefly interface for forward it to port 80 when browsing on your localhost.

**Pre-Requisites:** 
* Installed Docker
* Installed Docker Compose

### [File structure](![image](https://github.com/Hsanokklis/DockerMiniProject/assets/113212665/d4afa2f2-2b32-4dd8-9e2c-59d80109e24b)

**DockerProject**
* [docker-compose.yml](docker-compose.yml)
* .env
* .db.env
* .importer.env
* **nginx**
   * DockerFile
   * nginx.conf
### Helpful Tips and Commands

## Set up Firefly III Container

**Make a project directory** 

This is where you will place all of your project files and where docker will pull from to start your container. 

## Set up Nginx proxy 
