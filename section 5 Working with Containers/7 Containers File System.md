# 7 Containers File System        02:46:02         ..... 

# Persistent Data using Volumes .....


- Each container has it's own file system that is invisible to other containers 

# Let's start both containers ... 

> docker start c1 
> docker start c2

# Create a cmd window (different sessions) and execute the running containers on <the 'shell mode ... 'sh> 

> docker exec -it <containerID/randName>  sh 

- 1st  cmd window 
> docker exec -it c1 sh

- second cmd window
> docker exec -it c2 sh



# If we add a file in the project dir in on of  the contianer ... it's won't affect the other contianer (this container will know nothing about the change made in the other container ...) .....





<NB ... So 'Never 'store 'data 'in 'a 'container 'file 'system , we can do this using 'volumes >


































# NB ...... 

docker run   =    docker exec            .... only difference its tthat docker run is to start a new container , while docker exec it to run comands for a runnning container .....





