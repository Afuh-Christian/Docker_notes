# 1 Starting Containers             02:34:03            ... 

- Veiw images 

> docker images 

- remove some of the images ... 

> docker image rm .... 



# see running containers .../

> docker ps

- because a container is a process , but it's a special kind of process because it has it's files system provided by the image

# Let's run a new container using the react-app image .. 

> docker run react-app

- the problem with this is that when we exit from here , the container stopps ... 

# We need to run the container <in the 'DETACHED_MODE or 'BACKGROUND >   

> docker run -d react-app  

- this command runs the app ... in the background ... Now we can run other commands while this container is running .... 

# - if we check the running process ... we will see this container running .... 

> docker ps 


CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS      NAMES
9a39c7b1dbd1   react-app   "docker-entrypoint.s…"   41 seconds ago   Up 32 seconds   3000/tcp   frosty_faraday




IMAGE  = react-app 
container_id = 9a39c7b1dbd1
NAMES = frosty_faraday




# NB ... the last column has <a 'NAME ... docker gives a random name to their containers> 
- We can refercenc a container either by <it's 'NAME(randomly_given_by_docker) or it's 'CONTAINER_ID>


# But we can Also give our container a name when starting the image

- stop the other running container first before running this one ......


> docker run -d --name <randName> <ImageName>
> docker run -d --name blue-sky react-app


#  Now verify ... 
- we have a new container running with NAME = blue-sky ... 






