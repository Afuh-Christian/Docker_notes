# 10 Exposing Ports    01:58:21     ... 

- start this app ouside of docker ... 

> npm start 

 - the app is running on http://localhost:3000/
 - this port is open on the host


 # When we run the react-app inside a docker container  , the port  will be open just on the container not on the host 
- port is open on container 



# On the  same machine , we can have multiple containers running thesame image .. 
- All these containers will be listerning to port 3000 , but the port 3000 on the host will not be auto maped to these containers ..






<At some point ,.. we will learn  how to map a port on the host to the port on a container .... >   . ....








# Now back to docker ..... 
- In <the 'Dockerfile ... we need to specify a command to tell what 'port the 'app will be 'listerning on 

# Dockerfile
EXPOSE 3000 

- the EXPOSE command just tell use this container will eventually listern on port 3000

- so later when we properly run this app inside the docker container ? 
    - We know that we should map a port on the host to port 3000 on the container .... 

# Dockerfile 
FROM  node:14.19.3-alpine3.16
WORKDIR /app 
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 
EXPOSE 3000 