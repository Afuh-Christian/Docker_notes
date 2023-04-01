# 3 The Sample Web Application          03:05:19.824  

- We will use a real world app ... with a 
    - front-end 
    - back-end 
    - database 


- When we clone this project from the github repo ... we have to do alot of things to get the project running ... 
- With docker , we just have to run a single command 


# You'll see a file in the root of the project  <called 'docker-compose.yml which is used for composing a multi-container application >

- with the above file in the project ... we just run .... 

> docker-compose up

# Output .....   
vidly-frontend-1  | You can now view vidly-frontend in the browser.
vidly-frontend-1  |
vidly-frontend-1  |   Local:            http://localhost:3000
vidly-frontend-1  |   On Your Network:  http://172.18.0.4:3000
vidly-frontend-1  |
vidly-frontend-1  | Note that the development build is not optimized.
vidly-frontend-1  | To create a production build, use npm run build.




# when we run the above command ... everything is set up for us ... 
- downloading 
    - All dependencies 
    - Node js
    - mongo db 
- set's up servers etc ... 




# Now the app is up and running ... and can be accessed at port 3000

# NB ... we don't have to manualy insert movies in our database ... 
- We have a migration script that does that for us ... 
- So docker auto executes that migration script as part of bringing up the application .    