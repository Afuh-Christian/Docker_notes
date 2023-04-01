# 7 Running commands     01:55:28    ... 

- When we run this contianer ... 

> docker run -it react-app sh 

/app:#  

- we check the list of files and find out that we do not have the node_modules .... 
- we can run ..... 

> npm install   

- but we don't need to do this because if we are to work with a larger app that needs alog of steps to run the app ... we might end up with errors ....

# So we include the <npm install > command in <the 'Dockerfile>

# dockerfile .... 
RUN npm install 

- with the run comand , we can run any command that works on windows or linux .... 



# NB ... if we run ... 
RUN apt .... 

- we will get an erro because alpine linux does not use apt but rather apk

# Dockerfile  

FROM  node:14.19.3-alpine3.16
WORKDIR /app 
COPY . .
RUN npm install 




# Now rebuild the project ..... 

> docker build -t react-app . 



# check to see if the node_modules have been installed ... 

> docker run -it react-app sh 

/app:# 

> ls -1  

Dockerfile
hello.md
# node_modules
package-lock.json
package.json
public
src
yarn.lock



