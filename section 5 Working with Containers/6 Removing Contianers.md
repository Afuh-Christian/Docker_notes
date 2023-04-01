# 6 Removing Contianers  02:44:15    .. 

# There are two ways to remove a container ... 

# method 1 
> docker container rm <containerID/randName> 

# method 2 
> docker rm <containerID/randName> 

- <We could get 'Error = We can't running containers > 
- We can either stop the container and then remove it 
    
> docker stop  <containerID/randName>
> docker rm <containerID/randName> 

- Or use the force command 

> docker rm -f <containerID/randName> 


# Verify .. 
- To check all containers ....  

> docker ps -a  

or search for the container you deleted <using 'pipes > 
# NB ... this command only works <on 'LINUX> 
> docker ps -a | grep react-sample

# We can use the prune command to remove a stopped contianers .. 

> docker container prune 











