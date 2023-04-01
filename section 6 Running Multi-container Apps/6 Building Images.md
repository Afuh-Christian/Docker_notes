# 6 Building Images          03:21:40.098     

- <Docker compose is built ontop of docker engine... so everything we have done with docker engine like building images , listing them ,starting containers etc .... all these operations are also available using 'docker-compose 
    - The small difference is that these commands using <docker-commands will apply to the whole application>


- # see all docker-compose commands 

> docker-compose


# see all options on build 

> docker-compose build --help


# .............Now let's build our compose our fullstact app ... 


> docker-compose build



# Now check the images .... 
> docker images

REPOSITORY       TAG       IMAGE ID       CREATED         SIZE
vidly-frontend   latest    713c6422a4de   4 minutes ago   299MB
vidly-backend    latest    21ca595d3128   8 minutes ago   184MB











# we see that the mongo image was not pulled ... to do this ... 
- this commands also runs the app ...


> docker-compose up

vidly-frontend-1  | You can now view vidly-frontend in the browser.
vidly-frontend-1  |
vidly-frontend-1  |   Local:            http://localhost:3000
vidly-frontend-1  |   On Your Network:  http://172.18.0.4:3000
vidly-frontend-1  |
vidly-frontend-1  | Note that the development build is not optimized.
vidly-frontend-1  | To create a production build, use npm run build.

- Now verify ... 






















# NB ... when we use the  
> docker-compose build 
twice on thesame project ... the time time does not changes because of caching ... 

to force build a new project ... 

> docker-compose build --no-cache