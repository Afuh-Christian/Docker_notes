# 9 Copying files between Host and containers  .  02:53:32.011


- Sometimes we need to copy files between a host and a container ... for example  
    - Let's say we have a log files in our container and we want to bring it to the host and analyse it .. 

# check runnning containers 
> docker ps 
# Make a small change in the container .... 

> docker exec -it <containerID/randName> sh 
/app $ 
> echo hello > log.txt 
> exit 












# ________ CONTAINER TO HOST __________________________
# Let's copy the log.txt to the host ..... 
- <Now we wish to 'copy the 'log.txt file from the 'container to the 'host ... > 
 
cp = docker copy command 
 
> docker cp <source=(containerID/randName)>:<path_To_File_to_Copy>  <destination>

/app = WORKDIR in the dockerfile
. = current directory 

> docker cp nostalgic_volhard:/app/log.txt   . 


# Now if you check the current dir which is the directoy where your react-app is and the dir where your cmd is on .. type <the 'dir to see the 'log.txt file> 

since "ls" is a linux command and not a windows command ... 

> dir 

02/18/2023  10:11 PM    <DIR>          .
02/18/2023  10:11 PM    <DIR>          ..
02/11/2023  08:30 PM                38 .dockerignore
02/10/2023  07:51 PM    <DIR>          .git
03/05/2021  08:00 PM               310 .gitignore
02/14/2023  09:27 PM               263 Dockerfile
02/10/2023  08:24 PM               802 hello.md
# 02/18/2023  10:03 PM                 6 log.txt
02/11/2023  06:06 PM    <DIR>          node_modules
02/11/2023  05:50 PM           831,033 package-lock.json
03/05/2021  08:00 PM               813 package.json
02/10/2023  07:52 PM    <DIR>          public
03/05/2021  08:00 PM             3,362 README.md
02/10/2023  07:52 PM    <DIR>          src
02/11/2023  05:50 PM           492,932 yarn.lock















# ______________HOST TO CONTAINER_________________________

- create a file in the current dir 

> echo hello > secret.txt 

- Now we have a file on our project directory on our host ... 
- But this file is not part of the version controle system ..
<Now we want to 'manually 'copy this file into the container > 

> docker cp <path_to_file_to_be_copied> <containerID/randName>:<WORKDIR_of_project> 

> docker cp secrete.txt nostalgic_volhard:/app


# Now go to the container and check if the file was transfered successfully ... 

> docker exec -it nostalgic_volhard sh 
> ls -1

Dockerfile
data
log.txt
node_modules
package-lock.json
package.json
public
# secret.txt
src
yarn.lock



<a 'success> 

