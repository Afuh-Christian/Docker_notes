# 16 Sharing Images     02:25:39         ..... 

- Now let's see how we can share our images with others .... 

- Go to 

https://hub.docker.com/

- create a new account .... it's free .. and will  take seconds ...

# create <new 'REPOSITORY > ..... It's similar to creating a github repository  .........    02:26:20   .......

- In <one 'repository , we can have 'multiple_images>


# create repository .. 

repo name = react-app 
description = __ 
security = public   .... <for a free account , you can only create one private repository ...>

- <Otionally , we can connect our docker account to our github account so that everytime you do a 'push docker_hub auto 'pulls the 'latest code and 'builds a new image>
    - We won't do this now .... 

confirm create   ....







# Now to publish our images .... .

# view images .. 
>docker images 

REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
react-app    latest    3ceeeaf1c709   9 hours ago    446MB
react-app    v2        3ceeeaf1c709   9 hours ago    446MB
react-app    v1        341bb72204c2   11 hours ago   446MB
alpine       latest    b2aa39c304c2   27 hours ago   7.05MB
ubuntu       latest    58db3edaf2be   2 weeks ago    77.8MB

# we want to publish the latest version of the reac-app image .... 

- create a new tag for the latest image ... 

> docker image tag 3ceeeaf1c709 afuhchristian/react-app:v2


# view images ... 

> docer images

REPOSITORY                TAG       IMAGE ID       CREATED        SIZE
react-app                 latest    3ceeeaf1c709   9 hours ago    446MB
react-app                 v2        3ceeeaf1c709   9 hours ago    446MB
afuhchristian/react-app   v2        3ceeeaf1c709   9 hours ago    446MB
react-app                 v1        341bb72204c2   11 hours ago   446MB
alpine                    latest    b2aa39c304c2   27 hours ago   7.05MB
ubuntu                    latest    58db3edaf2be   2 weeks ago    77.8MB


# Now this image 3ceeeaf1c709 has 3 tags .... 

# Now we are ready to push the image .... afuhchristian/react-app

# step 1 login 

> docker login 

# step 2 push .. 

> docker push afuhchristian/react-app:v2

- The first push , pushes  all the layers in the docker file 
- In the next push ... asuming there are no changes in the dependency files (package*.json) ... the node_modules will not be pushed again 
- So the next pushes will be very fast ...




# Now let's make a change and try to push again .... 

- make change and build 

> docker build -t react-app:v3 . 

- Now will give this image and extra tag that starts <with 'afuhchristian/ , name of repo...>

> docker image  tag react-app:v3 afuhchristian/react-app:v3


-  now push ..

> docker push afuhchristian/react-app:v3


- <This push was faster since the other layers already exist> 


# Now in the repo ... we have two tags ... 

- v2 
- v3 




# Now that our image is on docker hub .... we can pull it on any machine that runs docker .....    

- <Just like 'pulling any other images from docker hub ....> 








