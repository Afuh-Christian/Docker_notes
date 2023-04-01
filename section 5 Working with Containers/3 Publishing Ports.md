# 3 Publishing Ports     02:39:12         ..... 

- so currently we have 2 containers running our react-app

- but if we go to http://localhost:3000 , we <won't be able to access the app .... >
- <Remember port 3000 is published on the container and not on the host >


# veiw the runnig images ... 

- theres a column called <PORTS>   ... you see the port that is published on the container .... 

> docker ps 

CONTAINER ID   IMAGE       COMMAND                  CREATED         STATUS         PORTS      NAMES
750fc28a6fe6   react-app   "docker-entrypoint.s…"   6 seconds ago   Up 2 seconds   3000/tcp   react-sample



- <PORTS = 3000/tcp>

# Now we will start a new container and publish a port at thesame time .... 



-p = port 

> docker run -d -p <portofhost>:<portofContainer>  
> docker run -d -p 4000:3000 --name c1 react-app




<Now if we go to 'http://localhost:4000 we will see our react-app with randName "c1 >
..... 

<a 'success ... the react-app was was displayed on chrome browser .... >



# Let's view running containers .... 

CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS                    NAMES
5567d67610c6   react-app   "docker-entrypoint.s…"   2 minutes ago    Up 2 minutes    0.0.0.0:4000->3000/tcp   c1
750fc28a6fe6   react-app   "docker-entrypoint.s…"   11 minutes ago   Up 11 minutes   3000/tcp                 react-sample


<from 0.0.0.0:4000->3000/tcp  , we see that port 4000 of host is mapped to port 3000 of container ....>