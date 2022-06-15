# Overview

This repository contains a boilerplate setup for building a website powered by
wordpress with nginx as the HTTP server and acting as the reverse-proxy. To run
wordpress, PHP-FPM is used to process PHP and MariaDB as the backend database.


# Setup

## Initialization

The following commands will configure the template project with a custom project
name.

    $ ./configure --project=myproj
    $ make

For a set of configuration options, use the help flag: `./configure -h`.


## Configuration

By default, `docker compose` reads environment variables from a file named
`.env` in the same path as the `docker-compose.yaml` file, which orchestrates
and configures the execution of the various docker containers.

Included is a `.env` file with default values set. When the project is
initialized, the `.env` will be removed from the repository cache as it contains
sensitive settings.

For more information on defining environment variables, see
[https://docs.docker.com/compose/env-file/](https://docs.docker.com/compose/env-file/)


# Launch

Run the following command as `docker-compose.yaml` to build the services:

    $ docker-compose build

At this point, you can now run the following command to start the
various docker containers:

    $ docker-compose up

(You may optionally run `docker-compose up --build` to achieve the same result
as above in one step)

When the containers are running, you may access the wordpress website from the
browser:

    http://localhost:8000

To stop the service, hit `Ctrl-c` from the docker container.


# Maintenance

## Administering the SQL Database

You can administer the SQL database by accessing the following address in your
browser:

    http://localhost:8080

Refer to the information in the `.env` file and the secret username and password
information stored in the `secrets/` directory.

## Launching Bash

You can launch a bash shell in the wordpress container with the following
command:

    $ docker container exec -ti <proj>_wordpress bash


# Resources

* [How to Install Wordpress with Docker Compose](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-docker-compose)
* [Install Wordpress with Docker Compose, Nginx, Apache with SSL](https://www.cloudbooklet.com/install-wordpress-with-docker-compose-nginx-apache-with-ssl/)
* [Understanding and Implementing FastCGI Proxying in Nginx](https://www.digitalocean.com/community/tutorials/understanding-and-implementing-fastcgi-proxying-in-nginx)
* [Understanding Nginx Server and Location Block Selection Algorithms](https://www.digitalocean.com/community/tutorials/understanding-nginx-server-and-location-block-selection-algorithms)
