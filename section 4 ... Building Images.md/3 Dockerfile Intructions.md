# 3 Dockerfile Intructions          01:38:02          .... 

# let's dockerise this react app ... 
# Dockerfile complete list of  options
- <d 'FROM = for specifying the base image , so we take that base image which contians a bunch of files and directories and then we build ontop of it  >
- <d 'WORKDIR = for specifying the working directory . Once we execute this command , all the following commands will be executed in the current working directory  >
- <d 'COPY = for copying files and directories >
- <d 'ADD = for copying files and directories >
- <d 'RUN = for executing OS commands ...., so all the linux command we talked about in the previous commands .. you can execute them using "RUN" >
- <d 'ENV = for setting environment variables > 
- <d 'EXPOSE = for telling docker that  our container is starting on a given port >
- <d 'USER = for specifying the user that should run the application....typically,  we want to run our app using a user with limited privilages>
- <d 'CMD = for specifying the command that should be executed when we start the container >
- <d 'ENTRYPOINT = for specifying the command that should be executed when we start the container>


# step 1  _________Add a dockerfile to it___________________
- Dockerfile contians intructions for building an image ... 




