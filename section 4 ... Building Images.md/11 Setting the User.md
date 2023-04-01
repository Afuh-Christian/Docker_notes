# 11 Setting the User ....  01:59:47  
- by default docker runs our app with the root user that has the highest privilages ..

- so that can open security holes in our system 

- So to create this app , we should create  a regular user with limited accesses 


# Before doing this on a docker file , open up a shell on alpine linux ...

> docker run -it alpine

# in alpine ... 
- no useradd ..... instead "adduser"


# Create a new user ..... 

> adduser
-G = setting the primary group ... 
-S = for creating a system user (it's not a real user ... just for running our app ..) 
    - Befor using this command , we have to create a group ... so we can add this user to that group .. 

# create group .... and add user to it ... 

> addgroup <groupname>
> addgroup peter
> adduser -S -G <groupname> <username> 
> adduser -S -G peter peter

- it's a good practice in linux for username and  their primary group name being thesame .... 

- check groups for peter ... 

> groups peter 
peter  



# we will combine the create group and create user into a single command .... 

> addgroup mosh && adduser -S -G mosh mosh 

- verify groups for mosh ... 

/ # groups mosh
mosh


# this is the command we will run in the dockerfile ....

# Dockerfile 
RUN  addgroup admin && adduser -S -G admin admin 
USER admin 

- <once we create the  user , we set the user using the 'USER command 
- <so all the following command will be executed using the 'USER  set above ...
>


# Dockerfile 
FROM  node:14.19.3-alpine3.16
WORKDIR /app 
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 
EXPOSE 3000 
RUN addgroup admin && adduser -S -G admin admin 
USER admin




# Now rebuild the image. ... 


> docker build -t react-app . 




# Let's start a new container , and make sure the current user is the app user and not the root user .... 

> docker run -it react-app sh 

/app $

- $ = any user .... # = root user .... so there's a difference now ... 

# print the current user's name ... 

> whoami
admin

- let's check the long listing and  see why <We executed this app a custom user and not the root user  >

> ls -l 

-rwxr-xr-x    1 root     root           224 Feb 11 18:41 Dockerfile
-rwxr-xr-x    1 root     root           802 Feb 10 19:24 hello.md
drwxr-xr-x 1066 root     root         36864 Feb 11 16:56 node_modules
-rwxr-xr-x    1 root     root        831033 Feb 11 16:50 package-lock.json
-rwxr-xr-x    1 root     root           813 Mar  5  2021 package.json
drwxr-xr-x    2 root     root          4096 Feb 11 10:01 public
drwxr-xr-x    2 root     root          4096 Feb 11 17:27 src
-rwxr-xr-x    1 root     root        492932 Feb 11 16:50 yarn.lock

- <the 'root user can 'r(read) , 'w(write) , 'x(execute)>
- <the 'custom user we made(admin) can only 'r-x  so , he can't edit anything .... > 
    - if we executed with the root user ... 
        - A hacker could potentially rewrite something in our app ...

- This is why You should always execute you images with a custom user ...