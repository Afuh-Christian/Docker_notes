# 10 Sharing the Source Code with a Contianer ... 02:55:53.014

- We have an app running at local host 5000 ... 
- Let's see how we can publish our application changes .... 


# PUBLISHING CHANGES 
# For production machines ..
 - We should always build a new image , tag it properly and then deploy . 

# For development machines .. (what we are currently doing ..) 
 - We don't want  to rebuild the image everytime we make a change in our code .
 - We can't also manually copy files everytime a change is made 






















# SOLUTION 
- <We can create a 'mapping or 'binding between a directory on the 'host and  a directory inside the 'container  >
    - <So this way any changes we make to any files in the 'host directory are 'immediately 'visible inside the container  >


# let's start a new container to demonstrate this .... 
- Early ,we used the volume mapping ... we used <the 'app-data volume>
    - <Using thesame 'syntax , we can 'map a directory on the 'host to a directory inside the container >
    - <We will use the name of the directory that holds our application in the place of the 'app-data .. >
    - we cannot type the full path , so we will use <the 'pwd command> 
        - if we just type pwd ... docker will think it's a named volume ... 
    - So <we have to wrapp the 'pwd in '$() to become '$(pwd)>
    - When we run it now ... $(pwd) will run first and return a full path to the working directory ... 
    - <Then we 'map it to the 'WORKDIR inside the container   .....   '$(pwd):/app >

> docker run -d -p 5001:3000 -v <PROJECTDIR>:<WORKDIR> <image>
We can create a volume if we wish to .... 
> docker run -d -p 5001:3000 -v <PROJECTDIR>:<WORKDIR> <image>  -v <volumeName>:<WORKDIR>

<fix ... 'This_does_not_work_on_windows....>

> docker run -d -p 5001:3000 -v $(pwd):/app react-app




# Let's look at the logs ... we'll use <the 'follow uption so that we can see the changes as they come up > 


> docker logs -f <containerID/randName> 
> docker logs -f   



Now the webserver is ready ... 







# In the next section , you'll <learn 'docker_compose , you'll see how easy it is to bring up an application with multiple components>





