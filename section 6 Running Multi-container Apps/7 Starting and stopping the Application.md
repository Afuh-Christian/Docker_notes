# 7 Starting and stopping the Application   03:25:17.206 

- We just saw how to start an application with docker compose ... 

> docker-compose up 

- If the images are ready ... docker compose will run them inside containers else it will auto build the images 


# ................Usefull Options ... 

> docker-compose up --help 

- <Build images before starting the containers >
- Force a rebuild 

> docker-compose up --build 

--build  =  up + build 

- <Run containers in background>

> docker-compose up -d 

-d = for detarched mode ... start the contianers in the background

- <To verify if these containers are running ... > 

> docker-compose ps 
- <We see all the conainers 'relevant 'to 'this 'application> 

vidly-backend-1     vidly-backend       "docker-entrypoint.s…"   backend             2 days ago          Up 12 minutes       0.0.0.0:3001->3001/tcp
vidly-db-1          mongo:4.0-xenial    "docker-entrypoint.s…"   db                  2 days ago          Up 12 minutes       0.0.0.0:27017->27017/tcp
vidly-frontend-1    vidly-frontend      "docker-entrypoint.s…"   frontend            2 days ago          Up 12 minutes       0.0.0.0:3000->3000/tcp


> docker ps 
- <we see all containers 'across 'all 'applications > 




# We have 3 containers  
vidly-backend-1
vidly-db-1
vidly-frontend-1

# Naming convention 
<projectname>-<servicename>-<ID>

With the <ID> , we can start multiple containers from thesame image and this is used for <high 'availability and 'scalability>


- In <the 2nd column> , we see the command that was used to start each project 
     - backend = npm start 
     - db =  mongodb 
     - frontend = npm start

- In <the 3rd column > , We see the <state , if the container is running ('up )>

- 4rd column , you see  port mapping ....



# Now if we are done with the application and we want to free up resources ... 

- this will stop and remove these containers

> docker-compose down

- But the image is still there , so next time we want to start the application , the application will start very quickly 


