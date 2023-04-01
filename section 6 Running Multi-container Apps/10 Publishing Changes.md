# 10 Publishing Changes          03:33:42           ..... 

- Obviously , we don't want to rebuild our application images everytime we change our code . 

- We will map the project directory e.g (backend) to the app directory inside our container exactly like before 

- This way , any changes we make in a directory are emidiately visible inside our container . 

- And we'll have to do same with the frontend dir separately 



# Step 1 ____ Open docker-compose.yml

- <Add a new properties in the backend called 'vol>
    - We can have one or more volume mapping ... we can either use the list or array syntax 

volumes:
    - <currenddir>:<workdir_of_image_in_container>
    - ./backend:/app


# docker-compose.yml

version: "3.8"

services:
  frontend:
    depends_on: 
      - backend
    build: ./frontend
    ports:
      - 3000:3000

  backend: 
    depends_on: 
      - db
    build: ./backend
    ports: 
      - 3001:3001
    environment: 
      DB_URL: mongodb://db/vidly
#   volumes:
#     - ./backend:/app
    command: ./docker-entrypoint.sh

  db:
    image: mongo:4.0-xenial
    ports:
      - 27017:27017
    volumes:
      - vidly:/data/db

volumes:
  vidly:

- <Now start the application > 

> docker-compose up 

# Output 
vidly-backend-1   | sh: nodemon: not found
vidly-backend-1   | npm ERR! code ELIFECYCLE
vidly-backend-1   | npm ERR! syscall spawn
vidly-backend-1   | npm ERR! file sh

# <You get an 'error that 'nodemon is not found>
- It's not in the image ... but it's in the project 

# Reason 
- Node module are not in the project dir (.backend) because we haven't installed npm dependencies on the host machine 
- These dependencies were only installed inside the docker container
- but now that we are sharing the application code with a container, the container sees the ./backend dir without the node_modules 

# To fix this  

> cd backend 
> npm install 


# Now try again 

> docker-compose up 

# Output 
[nodemon] starting `node index.js` 

<a 'success .... we can work on our project now .... >


# On browser .....   http://localhost:3001/api/

- <Go to the project dir on this machine and try to make a change in index.js and then refresh the browser ... it 'works > 


# .... Apply thesame technique on the frontend ..... 




