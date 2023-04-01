# 1 Images and Containers   01:32:14    ... 

# IMAGE 
- An image includes everything an application needs to run .. 
- It contains a 
    - A cut-down  OS 
    - Third-party libaries
    - Application files 
    - Environment variables 
    etc 
- it contains all the files and config settings needed to run our app ..
- Once we have an IMAGE ,  we can start a container from it 



# CONTAINER
- Provides an isolated environment for executing an application 
- Can be stoppend & restarted 
- Is just a process
    - but a special kind of process because it has it's own 
    file system which is provided by the image




# While the current ubuntu container is running ,, try starting a new IMAGE and see what happens ... on a new terminal window ..... 

- check to be sure if the other image is running ... 
> docker ps 

- if it is the start a new one and see what happens .. 
> docker run -it  ubuntu

root@91fb01b8f80f:/#

we get a new container ... 

# The contents of both containers are different ... 
- since we just created a new one , and some modifications have been done on the old container ... 

# This is Because .... 

<A 'container gets its file system from the 'image , but each container has its own 'right-layer> 
    - What we write in a given container is invisible to other containers ... (but there's a way to share data between contianers)
