# 12 Running Tests      03:45:07          ......

- A Bunch of unit and intergration test have been written in this project frontend  ... 

# Try running the test on the host ... 

> cd frontend
> npm test 

- press "q" to exit  ............










# How to run test inside container .... (This is slow !!) 
- <We will create a new service in the 'docker-compose files called 'frontend-tests >

- We woun't build because we will be using an existing image 

frontend-tests 
    image:<image_name>
    image:vidly_frontend

- We will override the command for this image and run "npm test"

frontend-tests 
    image:vidly_frontend
    volumes:
        - ./frontend:/app 
    command:npm test



# docker-compose.yaml 

version: "3.8"

services:
  frontend:
    depends_on: 
      - backend
    build: ./frontend
    ports:
      - 3000:3000
 
# frontend-tests:
    image: vidly_frontend
    volumes:
        - ./frontend:/app 
    command: npm test
# ...................................
  backend: 
    depends_on: 
      - db
    build: ./backend
    ports: 
      - 3001:3001
    environment: 
      DB_URL: mongodb://db/vidly
    volumes:
      - ./backend:/app
    command: "./docker-entrypoint.sh"

  db:
    image: mongo:4.0-xenial
    ports:
      - 27017:27017
    volumes:
      - vidly:/data/db

volumes:
  vidly:



- <Leave the frontend dir and compose the app .. > 

> cd .. 
> docker-compose up 





# The application is up and we can see the output of our web container ..... 


- we see the test cases and results ... 

- When a change is made in the code base ... it takes a while intill the test are re-run

# The advantage of this method is that <You do not need to open a different window an run frontend and backend separately> 






# So we can do same for backend test ... 
- creating a service for it ...etc
- So that we see both the results of the front end and backend all in one window ...





