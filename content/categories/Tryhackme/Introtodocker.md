---
title: "Intro To Docker"
date: 2023-08-14T17:07:49+05:30
draft: false
---



## Basic Docker Syntax

1. if we wanted to `pull` a docker image, what would our command look like?
    
    ```jsx
    docker pull
    ```
    
2. If we wanted to list all images on a device running Docker, what would our command look like?
    
    ```jsx
    docker images ls
    ```
    
3. Let's say we wanted to pull the image "tryhackme" (no quotations); what would our command look like?
    
    ```jsx
    docker pull tryhackme
    ```
    
4. Let's say we wanted to pull the image "tryhackme" with the tag "1337" (no quotations). What would our command look like?
    
    ```jsx
    docker pull tryhackme:1337
    ```
    

## Running First Container

1. What would our command look like if we wanted to run a container **interactively**?
    
    ```jsx
    docker run -it
    ```
    
2. What would our command look like if we wanted to run a container in "**detached**" mode?
    
    ```jsx
    docker run -d
    ```
    
3. Let's say we want to run a container that will run **and** bind a webserver on port 80. What would our command look like?
    
    ```jsx
    docker run -p 80:80
    ```
    
4. How would we list all **running** containers?
    
    ```jsx
    docker ps
    ```
    
5. Now, how would we list **all** containers (including stopped)?
    
    ```jsx
    docker ps -a
    ```
    
    ## Intro to Dockerfiles
    
    1. What instruction would we use to specify what base image the container should be using?
        
        ```jsx
        From
        ```
        
    2. What instruction would we use to tell the container to run a command?
        
        ```jsx
        run
        ```
        
    3. What docker command would we use to build an image using a Dockerfile?
        
        ```jsx
        build
        ```
        
    4. Let's say we want to name this image; what argument would we use?
        
        ```jsx
        -t
        ```
        
    
    ## Intro to Docker Compose
    
    1. I want to use `docker-compose`  to **start up** a series of containers. What argument allows me to do this?
        
        ```jsx
        up
        ```
        
    2. I want to use `docker-compose`  to **delete** the series of containers. What argument allows me to do this?
        
        ```jsx
        down
        ```
        
    3. What is the name of the .yml file that `docker-compose` uses?
        
        ```jsx
        docker-compose.yml
        ```
        
    
    ## Intro to the Docker Socket
    
    1. What does the term "IPC" stand for?
        
        ```
        Interprocess Communication
        ```
        
    2. What technology can the Docker Server be equalled to?
        
        ```
        api
        ```
        
        ## Practical
        
        1. Connect to the machine. What is the name of the container that is currently running?
            
            ```
            cloudisland
            ```
            
        2. Use Docker to start a web server with the "webserver" image (no quotations). You will need to **run the container with port 80**.
            
            ```
            ?
            ```