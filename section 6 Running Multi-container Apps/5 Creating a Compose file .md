# 5 Creating a Compose file       03:12:42.412

- Creating a compose file from scratch ...... 


# Rename the old file to <a '_docker-compose.yml  to ignore it .. 


# Now create your compose file .. 

- <a 'docker-compose.yml>


# 1st ____ set the version  

https://docs.docker.com/compose/compose-file/ 

- You see the various compose file format version and the compatible docker engine release 
    - take the version that will suit you docker engine 
- <NB ... make use the number is in a 'double_quotes else docker will evaluate this as a number > 


# docker-compose.yml
version:"3.8"




















# 2nd _______build _&__pull___  we define <various building blocks for services of our application>

services:
    frontend:
    backend:
    database: 

- the  name  of these services can be anything .. 

services: 
    web:
    api:
    db:

- <The idea here is that .... we are defining various services and telling docker how to 'build 'images for 'each 'service and how to run these images >
    - <for each service , we will have properties and the value of thes properties will eventually be used when running the container>
    - <previously , we used 
        > docker run <imagenme>  ... etc 
    to run and image ... 
        Now all this can be put within the properties of the services .... 
    - So we don't have to manualy start the containers ... docker-compose starts the containers under the hood ... 
    - <So for each service , we have to tell docker how to 'build an 'image for that service .>
    - <Each service should have it's own 'DOCKERFILE > 
    
services: 
    web:
        build:<path_to_dockerfile>
        build: ./frontend
    api:
        build: ./backend
    db:
        <No build ... we will pull and 'image for mongodb from dockerhub>
    

services: 
    web:
        build: ./frontend
    api:
        build: ./backend
    db:
        image: mongo:4.0-xenial

<mongo:4.0-xenial is mongo --version '4 'build ontop of 'xenial which is 'ubuntu --verson '16>
    - in dockerhub ... mongo also has images built ontop of windows, but windows images are very large , over 2gb 













# 3nd  ___ port ____ mapping 
- represented as list


services: 
    web:
        build: ./frontend
        ports:
        - <host>:<Container_Running_the_image> 
    api:
        build: ./backend
    db:
        image: mongo:4.0-xenial
        ports:
        - <host>:<default_port= '27017>



services: 
    web:
        build: ./frontend
        ports:
            - 3000:3000
    api:
        build: ./backend
        ports:
            - 3001:3001
    db:
        image: mongo:4.0-xenial
        ports:
            - 27017:27017 


<we use '27017 so we can access mongodb using a 'mongodb_client like 'compass .... thesame concept applies to other database engines ...>
- <All database engines have a 'default_port ... you wish to map that port so you can connnect to the database engine using the db client of your choice>





# 4th ___ environment variables ____ 

- The api project needs and environnment variable to tell where the database is (a <mongodb connection string>)
- we can use the list syntax because we can have multiple environment variables  


services: 
    web:
        build: ./frontend
        ports:
            - 3000:3000
        environment: 
            - DB_URL=<mongodb connection string>
            - DB_URL=mongodb://<hostName>/<databaseName>
            - DB_URL=mongodb://db/vidl
    api:
        build: ./backend
        ports:
            - 3001:3001
    db:
        image: mongo:4.0-xenial
        ports:
            - 27017:27017 


- when we start an <app with 'docker-compose , a 'network is created ... on this network , we are going to have '3 'host which are 'db , 'api , 'web >

- <We can also use the 'property:value syntax>

services: 
    web:
        build: ./frontend
        ports:
            - 3000:3000
        environment: 
#            DB_URL: mongodb://db/vidl
    api:
        build: ./backend
        ports:
            - 3001:3001
    db:
        image: mongo:4.0-xenial
        ports:
            - 27017:27017 





# 5th________volume_________

- We don't want mondodb to write data to the temporary file system of the container 

- we will map a volume called "vidly" to a dir inside the contianer 
    - by defualt , <mongodb stores it's data in /data/db >




services: 
    web:
        build: ./frontend
        ports:
            - 3000:3000
        environment: 
#           DB_URL: mongodb://db/vidl
    api:
        build: ./backend
        ports:
            - 3001:3001
    db:
        image: mongo:4.0-xenial
        ports:
            - 27017:27017 
#       volumes: 
#           - vidly:/data/db



# NB ... we have to define the volume first before we can use it ... 



services: 
    web:
        build: ./frontend
        ports:
            - 3000:3000
        environment: 
            DB_URL: mongodb://db/vidl
    api:
        build: ./backend
        ports:
            - 3001:3001
    db:
        image: mongo:4.0-xenial
        ports:
            - 27017:27017 
volumes:
    vidly:
















# docker-compose.yml
version: "3.8"

services:
  frontend:
    depends_on: 
      - backend
    build: ./frontend
    ports:
      - 3000:3000

  backend: 
    depends_on: 
      - db
    build: ./backend
    ports: 
      - 3001:3001
    environment: 
      DB_URL: mongodb://db/vidly

  db:
    image: mongo:4.0-xenial
    ports:
      - 27017:27017
    volumes:
      - vidly:/data/db 

volumes:
  vidly:
