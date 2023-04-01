# 2 Cleaning Up Our Workspace   03:02:11.953

# Techniques for cleaning up the workspace ... 

# Remove image(s) 

> docker image rm <imageName/imageID>
for multiple images 
> docker image rm <imageName/imageID> <imageName/imageID> <imageName/imageID>

# See all images 

> docker image ls
 
# get all image IDs 

> docker image ls -q 

# Now we can pass this as an element to docker image remove 

> docker image rm $(docker image ls -q) 

- Running this will give and error because some of the images are in running or stop containers ... 
- For now we will delete all containers with a similar command .. 

> docker container rm $(docker container ls -q) 

or return an remove all containers including stop containes ... 

> docker container rm -f $(docker container ls -a -q)  
> docker container rm -f $(docker container ls -aq)  

You have to add the force command so we can remove running containers as well ... 

> docker container rm -f $(docker container ls -aq) 





# NB .... <the '$() command does not work on windows .... research on an alternative method ... >







# Docker desktop ... .03:04:33.359