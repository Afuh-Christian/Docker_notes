# Persistent Data using Volumes  ...    02:47:36      ....

# VOLUMES 
- A volume is a storage outside of contianers 
- It can be a directory on the host or somewhere on the cloud

# How to work with volumes ..... 

- To see the commands available for volumes .. 

> docker volume

# Output .... 
Manage volumes

Commands:
  create      Create a volume
  inspect     Display detailed information on one or more volumes
  ls          List volumes
  prune       Remove all unused local volumes
  rm          Remove one or more volumes


# Create a new volume called "app-data" 

> docker volume create <volumeName>
> docker volume create app-data


# Now let's inspect the volume we created to see the properties it has .... 

> docker volume inspect <volumeName>
> docker volume inspect app-data

# Output ... 

[
    {
        "CreatedAt": "2023-02-13T21:31:33Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/app-data/_data",
        "Name": "app-data",
        "Options": {},
        "Scope": "local"
    }
]

# Meaning of properties ... 

   "Driver": "local",        <it's a directory on the 'host ... We also have 'Drivers for creating volumes in the 'cloud  (So if you use a cloud platform ,you need to do your own research and find a driver for creating a volume in that cloud platform ...) >

   "Mountpoint": "/var/lib/docker/volumes/app-data/_data", <This is where the directory is created on the 'host ... (this is a linux path ... if it were windows ... it'll be like c:// ....)>



# Let's see how we can start a container given this volume for persistent data .... 

-v = volume 

> docker run -d -p 4000:3000 -v <volumename>:/<WORKDIR>/<NewDir> <IMAGE>

> docker run -d -p 4000:3000 -v app-data:/app/data react-app
4c39f1bba6b804a4a490371a3a806fed5f2e610671b3582a22c2984e51d12491          


# let's run a shell session ... 

> docker exec -it  4c39f1bba6b804a4a490371a3a806fed5f2e610671b3582a22c2984e51d12491 sh

/app $

- <Now check files and folers ... you see the 'NewDir created> 

> ls -1 

- Enter data and do some changes .... 

> cd data 
> echo data > d.txt 
# output .... 
sh: can't create d.txt: Permission denied


- <Nb .. you can verify the permissions with the long listing .... > 

> ls -l 

-rwxr-xr-x    1 root     root           247 Feb 11 21:12 Dockerfile
-rwxr-xr-x    1 root     root     498295808 Feb 12 10:07 V4
drwxr-xr-x    2 root     root          4096 Feb 13 21:31 data
drwxr-xr-x    1 admin    admin         4096 Feb 14 19:53 node_modules
-rwxr-xr-x    1 root     root        831033 Feb 11 16:50 package-lock.json
-rwxr-xr-x    1 root     root           813 Mar  5  2021 package.json
drwxr-xr-x    2 root     root          4096 Feb 11 10:01 public
drwxr-xr-x    2 root     root          4096 Feb 12 09:20 src
-rwxr-xr-x    1 root     root        492932 Feb 11 16:50 yarn.lock


- <The owner is the only user that has 'right_permision , so the app user(user that runs the app) belongs to the 'others_group and in this group , we don't have the 'rights_permission>

- <The reason for this 'issue is because we let docker auto create the '/data directory for us >

- <So to prevent this from happening , we have to go to our 'Dockerfile>

WORKDIR /app 
RUN mkdir data

- <So we'll be creating this directory using the app user we defined earlier in this file .... > 

- <So by this ... the '/data dir will be owned by the admin user and will 'auto have the 'rights_permission.>   

# Dockerfile 
FROM  node:14.19.3-alpine3.16
RUN addgroup admin && adduser -S -G admin admin 
USER admin
WORKDIR /app 
RUN mkdir data
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 
EXPOSE 3000 
CMD [ "npm","start"] 

- Now we have to  rebuild the dockerfile .... 

> docker build -t d1 . 

# Now run a new  container with a given volume ... we still create <the 'data dir , but this time it already exist and the 'admin user owns this directory > 


> docker run -d -p 2000:3000 -v app-data:/app/data react-app 
67928d2a54dfe69a5266781728c9c5ed1d96aa51a78eeb50b5b67b53c6d38ffe

# Now let's run a short session inside this container .. 
- Then try making a change again .. 



> docker exec 67928d2a54dfe69a5266781728c9c5ed1d96aa51a78eeb50b5b67b53c6d38ffe sh

/app $ 

> cd data 
> echo data > d.txt

- <Now here's the magic about 'VOLUMES .... = IF we delete the current container containing the new change we just made ... the change will 'persist (if we created a file in a container inside a volume and delete that contianer ... the file will still exist ... )>
   - The the <new file created will still exist because .... the '/data dir is stored 'outside 'of the contianer , it's actually a directory on the 'host  >

# Now let's remove this container and see if <the 'd.txt go deleted ...>


> docker rm -f <containerID/randName>
> docker rm -f 67928


# Now Let's start a new container with <thesame 'volume_mapping>  ... 

> docker run -d -p 5500:3000 -v app-data:/app/data react-app 
ab817200720758c85187e2c027cb8dfe274ab36f034e38ba071ef8093a9cdb99

- The run a shell session to check the file system ....    

> docker exec -it <containerID> sh 
> docker exec -it ab817200720758c85187e2c027cb8dfe274ab36f034e38ba071ef8093a9cdb99 sh 
/app $

- <check the 'd.txt file that was in the container that was deleted .. > 

> cd data 
> ls 
d.txt 


<So the file still exist in this new container .... > 

- if you delete a container , <the associated 'volume is not deleted ..> 

<NB .... We can 'Share-Volume amongst multiple containers >
