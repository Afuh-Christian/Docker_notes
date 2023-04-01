# 4 Executing Commands In Running Containers       02:41:20 ..

- When we run our container , it execute the defualt command we set in our docker file ... <CMD ["npm" , "start" ]>

# What if we want to execute a command in a running container LATER ON ..... 
- Eg .. we want to troubleshoot something and we want to look at the file system of that container ... 

# how it's done .. 


- <with this command we can execute commands in a running container >

> docker exec  

> docker exec <randName/containerID>  <any_OS_or_Linux_command>
> docker exec c1 ls 

# Output .. 
Dockerfile
V4
node_modules
package-lock.json
package.json
public
src
yarn.lock


<We see the content of our app dir>
<All these command run in the 'app 'dir because ... in the DOCKERFILE ... WE SET   =  WORKDIR /app  ..... that's why we we ran 'ls  , we just saw the content of that dir .... 
 >



# We can also open the app in the shell mode ....  

> docker exec -it c1 sh 

/app $ 

# even when we exit the shell ... it doesn't change the state of our container ... the container will still be running ... 




# NB ... <so using the 'exec command , we can execute any command in a running container ..... >

































# docker run 
    - start a new container and run a command

# docker exec
    - Execute a command in a running container 