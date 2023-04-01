#  12 Defining Entrypoints     02:04:37       ..... 

- The Dockerfile is almost ready .... but how do we start the application ...

- In project directory , we can run  (  ) 
> npm start
- So this is the command that we should execute when startin a container ... 

# .............we will not run in an interactive mode because we do not want to interact with the app ... 

> docker run react-app 

# Our container started and then stopped ,  becuase we haven't specified a command or programe to execute 

> docker run react-app npm start 

Failed to compile.

EACCES: permission denied, mkdir '/app/node_modules/.cache'

# We get <a 'permission_denied .... this is because in the Dockerfile ... we ran all the main commands with the root user and then switched to a new custom user with limited privilages .... so we have to move the part where we set the new user to the top and then rebuild the image .... >

# Dockerfile ....  edited ... now all the commands to create the image will be done with the custome user .. admin ...
FROM  node:14.19.3-alpine3.16
# RUN addgroup admin && adduser -S -G admin admin 
# USER admin
WORKDIR /app 
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 
EXPOSE 3000 


# Now rebuild to apply the above changes .... 

> docker build -t react-app .

# Now when you start the app in the container ... it run successfully .... 

> docker run react-app npm start  

# Also ,.... we don't want to specify the full command everytime we want to run the react-app in the container ... 

- we will use <the 'CMD instruction  and supply a defualt command to be executed .... 

# Dockerfile 
CMD npm start


# Dockerfile 
FROM  node:14.19.3-alpine3.16
RUN addgroup admin && adduser -S -G admin admin 
USER admin
WORKDIR /app 
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 
EXPOSE 3000 
CMD npm start

# NB ... <If there are multiple 'CMD , only the last one will be executed ...>

# Now rebuild the image to add this .... 

> docker build -t react-app .

# Now we can run the container by simply runing ... 

> docker run react-app 

Compiled successfully!

You can now view react-app in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://172.17.0.2:3000





# NB .... This is port 3000 of the container .... if we visit the  localhost of our machine , we won't access the address location...




# Next we will map a port from the host to a port from the container ...... 


































# RUN 
- Is a built time instruction . 
- It's executed at the time of building the image
 
# CMD  
- Is a run time instruction 
- It's executed when starting a container .
- It has two forms ... 
    - # shell form 
    CMD npm start 
        - docker will execute this command inside a separate shell ... ei (shell form)
        - on linux shell ... /bin/sh
        - on windows   ..... cmd
    - # Execute form 
    CMD ["npm","start"] 
        - This is a common practice 
        - Because with this we can execute the command directly and there's no need to generate another shell process 
        - Also , this makes it easier and faster   to clean up resources when you stop containers ...
        - <So always use the 'Execure_form>


# Dockerfile ... 
FROM  node:14.19.3-alpine3.16
RUN addgroup admin && adduser -S -G admin admin 
USER admin
WORKDIR /app 
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
ENV API_URL=http://api.myapp.com/ 
EXPOSE 3000 
CMD [ "npm","start"] 




















# We also <have 'ENTRYPOINT  which is very similar to 'CMD> 
- It also has 2 forms ....
    - # shell form 
    ENTRYPOINT npm start 
        - docker will execute this command inside a separate shell ... ei (shell form)
        - on linux shell ... /bin/sh
        - on windows   ..... cmd
    - # Execute form 
    ENTRYPOINT ["npm","start"] 
        - This is a common practice 
        - Because with this we can execute the command directly and there's no need to generate another shell process 
        - Also , this makes it easier and faster   to clean up resources when you stop containers ...
        - <So always use the 'Execure_form>









# CMD .... 
- We can overide the default command that was set 
CMD npm start  

> docker run react-app echo hello  

- "hello" will be printed on the terminal an the react-app will not start .   



# ENTRYPOINT .... 
- We can't overide the default command set  unless we add the   --entrypoint

> docker run react-app --entrypoint echo hello 

# So it's very difficult to override the entry point ... 
# So you use ENTRYPOINT  when you want your app to be executed by only one command .... 

# You use CMD ... when you feel like you may user another command to run your app .... 



































