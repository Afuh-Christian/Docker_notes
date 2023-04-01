# 4 Choosing the Right Base Image ... 01:39:23   ..

# STEP 1 .. add Dockerfile to project root

.git
.gitignore
# Dockerfile
package.json
public
README.md
src
yarn.lock

# Dockerfile  
FROM <baseimage>

or 


<so 'baseimage = can be and OS like linux or windows or it can be an    'OS + 'runtime_environment>
- <runtime_env for some languges> 
    -  C# = .net image
    -  python = python image
    -  js = node image

# check docker samples to see various samples of dockerfiles ...  01:40:00

https://docs.docker.com/samples




# for this project ..... we need to use node .... 0141:00

- https://hub.docker.com/
- search node
- go to tags to see the various images ... 
 FROM node
- if you just type node ... docker will asume latest ... ant that is dangerous ... always use a specifice version
 FROM node:<version>
 - search the versions in the tag section ...
 - search for the ones with alpine so that they should be small ..

 type "alpine" in the search bar .. .

 - copy the version that suits u .... 

 <d FROM node:14.19.3-alpine3.16


# Dockerfile
FROM node:14.19.3-alpine3.16



# Step 2 ._____________build the image ________________

> docker build  -t <taganme> <directorytofinddockerfile>
e.g in current dir

> docker build -t react-app .

# checkk the images we have on this machin 
> docker images 
or 
> docker image ls

hello-docker   latest    5dba029975f2   5 days ago     176MB
<none>         <none>    047756bd07e0   8 days ago     176MB
ubuntu         latest    58db3edaf2be   2 weeks ago    77.8MB
react-app      latest    72436c3602b4   8 months ago   119MB

- the <reac-app> is the one we just  brought in ....

# try running the image .... in the iteractive mode .. 

> docker run -it react-app

# Output ..
Welcome to Node.js v14.19.3.
Type ".help" for more information.
>

- Now we are inside the node environment .... here we can write js code ....
- we do not want this 
- we will exit this node environment ... crtl + C 

# We will run bash so we can look at the file system ... 

> docker run -it <imagename> bash
> docker run -it react-app bash

# Ouput ....
we get and error <Error "module_not_found = this is because 'alpine-linux does not come with 'bash , that is why it is a very small linux distribution  ..... rather it comes with 'shell(the_original_shell_program)>

# So we will run shell since alpine comes with <only 'sh> 

> docker run -it  <nameofimage> sh
> docker run -it  react-app sh

# Output 
/ #

- Now we have <a 'shell_session running ... and we can pass commands to it .... >
    - Most the commands we run <in 'bash also run in 'sh

- <So we are in 'alpine-linux and the IMAGE also have 'node ....> 
    - You can check the node version in <the 'sh prompt by typing> 

    - > node --version

    - From <the 'sh prompt , you can still enter or exit the node environment >  
- In this image , we <dont have our 'application-files , we only have 'alpine-linux and 'node> 

