# 6 Docker in Action          00:17:43          .. 

- create new folder for project ... 
> mkdir hello-docker 
> echo console.log("Hello") > app.js 

# - Let's say we want to <dockerise> the small app we have above ... 
- we want to <build> , <run> , <ship> it using docker
(typically to run this app on another pc , we would have to install node and then run <node app.js> )


# Instructions for deploying this particular program .. 
- <Start with an OS> 
- <Install Node> 
- <Copy app files>
- <run node app.js> 

# disadvantage
- so we have to follow 4 steps just for a simple program 
- What if we had a more complex app ... we would have to make a complex documentation that would have to  be precisely followed ...          
- <this is where 'DOCKER 'COMES 'TO 'HELP>

# ... 
- we can write the 4 steps above inside a docker files and let <docker> package our application










# Procedue ... 

# Step 1  ____________________________________________
- <Add new file to project called 'Dockerfile> (install docker vscode by microsoft)
- <write instructions for packaging the app in the 'Dockerfile>
    - we start from a base image (this base image has a bunch of files )     
    - we will take those files and add additional files to it (like inheritance in programming )      
- <Base IMAGE> 
    - FROM linux image 
        - install node ontop of it 
    Or
    - FROM node image (this image is already built ontop of linux)
# NB .. This <IMAGES>  are officially published on <docker-hub>

- https://hub.docker.com
- search for node ... You'll find it there .... 

- <Docker hub> is a registry for docker images .... 
- There are multiple node images on the docker hub (these node images are built ontop of different distributions of linux )


# step 2 __________________________________________
# dockerfile 
FROM node:alpine 


<: > = to specify which linux  destribution we want to use 
<alpine> = a small linux distributions , so the size of the <Image> that we are going to download and <build> ontop of will be very small 


# step 3 ______________________________________________ 
- We start from that <IMAGE> 
- Then we need to  <copy> our app or program files ... 
    - copy all files in current directory, into app director , into that <IMAGE>
COPY ./app
    - The <IMAGE> has a file system , and in that file system , we will create a directory called </app>

# step 4 ______________________________________________
- Finally ,we'll use the <command instruction> to execute the command <node app/app.js(because app is inside the directory as set in COPY above ... )> in this case ...       

CMD node app/app.js 
OR ............
WORKDIR /app 
CMD node app.js

# Dockerfile 
FROM node:alpine 
COPY ./app 
CMD node app/app.js 

# ..........OR ...........

# Dockerfile 
FROM node:alpine 
COPY ./app
WORKDIR /app 
CMD node app.js



<the above instruction clearly document the deployment process> 



# step 5 ___________________________________________ 
- go to the terminal and tell docker to package the app ....
- We need to give our <IMAGE> a <tag to identfy it>   
- we need to specify where docker can find a dockerfile 

> docker build -t <repositoryname> <directorytofinddockerfile> 
e.g 
> docker build -t hello-docker . 

-t = creating a tag 
hello-docker = tagname 
. = dockerfile can be found in current directory ... 


# step 6 ___________________________________________ 
- to see all <IMAGES> on this computer .

> docker images
or 
> docker image ls
# output.. 
REPOSITORY     TAG       IMAGE ID       CREATED      SIZE
hello-docker   latest    047756bd07e0   2 days ago   176MB



# NB
- The  tagnames are given by default ... 
- these tages are used for versioning the docker ..
- <Each image can contain a different version of our application>
- <Each image has a unique ID>
- <we can see when the image was created > 
- <size of the image is displayed > 

# Because we used LINUX and NODE:ALPINE 
- <we used just 112MB of data>
- so the image contains 
    - node    
    - alpine linux   
    - application files 
an all that summed up to 112mb

# If we used a different node image based on a different distribution of linux 
- we would end up with a larger image       
- And when deploying that image , we would have to transfer that image from one pc to another 


# step 7 _____________________________________________
- Now we can run this <IMAGE>  on any computer runing docker 
- we can run from anywhere in the machine ... eg ..this one .. 

> docker run hello-docker 



# step 8 ______________________________________________
- We can <publish this IMAGE to docker-hub> so that anyone can use this image 
- Then we can go on another machine and <pull> and run this <IMAGE>  






























# We can use a test machine on this website ...  00:25:04 .... 


play-with-docker ..... 

https://labs.play-with-docker.com/

sign-in with docker ID .. 
- test the play ground if node is installed so that you'll be sure everything is running from the contianer
- And new instance 


# step 9 pulling ____________________________________________


> docker pull <dockerusername>/<repositoryname> 
e.g 
> docker pull codewithmosh/hello-docker

# to check if we have the repo in our machine ... 

> docker images
or 
> docker image ls

# NB
- The  tagnames are given by default ... 
- these tages are used for versioning the docker ..
- <Each image can contain a different version of our application>

# to run .... 

> docker run <dockerusername>/<repositoryname>
or 
> docker run codewithmosh/hello-docker











# Summary .... 
- We can take any app and dockerize it by adding a <Dockerfile> to it ... 
    - Dockerfile contains instruction for packaging our application into and <IMAGE> 
- once we have the <IMAGE>  we can run it anywhere (any machine with docker )