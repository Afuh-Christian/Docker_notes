# 11 Migrating the Database     03:37:46.620     ...

- Most of the time when we release our application , we want the database to be in a particular shape with some data , 
    - <This is called 'Database_migration>

- In this backend project ,... the database migration tool is <called 'migrate-mongo> 

# migrate-mongo-config.js

- if we check the package.json in <the 'devDependencies >

  "devDependencies": {
    "jest": "^26.6.3",
#     "migrate-mongo": "^8.1.4",
    "nodemon": "^2.0.7", 
    "supertest": "^6.1.3"
  },


# How migrations work .... 03:38:20

- Using the migrate-mongo ... we can create database migration scripts 
- In this project .. <the 'migration_scripts are stored in the 'migrations folder >


# migrations/20210208213312-populate-movies.js

module.exports = {
  async up(db, client) {
    await db
      .collection("movies")
      .insertMany([
        { title: "Avatar" },
        { title: "Star Wars" },
        { title: "Terminator" },
        { title: "Titanic" },
      ]);
  },

  async down(db, client) {
    await db.collection("movies").deleteMany({
      title: {
        $in: ["Avatar", "Star Wars", "Terminator", "Titanic"],
      },
    });
  },
};


- <So async 'up is for creating the database>
    - We go to the movies collections 
    - Insert the given movie objects as above 
- <So async 'down is for downgrading the database>
    - We remove the movies in the list


# Look at migrations folder and execute all migrations script 

> migrate-mongo up

- NB ... migrate-mongo does not execute a script multiple times 


- <In the 'package.json ... in the 'script section > 
    - we have a set of commands which <are 'aliases for the commands the represent .... >
  "scripts": {
    "db:up": "migrate-mongo up",
    "start": "nodemon --ignore './tests' index.js",
    "test": "jest --watchAll --colors"
  },


# So ...

> migrate-mongo db 
or 
> npm run db:up














# How do we execute the database migration as part of starting the application 



# Open the dockerfile for the backend project ... 

# Dockerfile
FROM node:14.16.0-alpine3.13

RUN addgroup app && adduser -S -G app app
USER app

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . . 

EXPOSE 3001 

# CMD ["npm", "start"]


- <A command in the 'Dockerfile can be overwritten in the 'docker-compose.yml file ..... e.g ... let's override the 'CMD command  >

# docker-compose.yml

services: 
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
#   command: migrate-mongo up && npm start



- <There's a 'PROBLEM with the above command since the mongo database usualy takes time to set up ... so we will have to wait for the mongodb on the host before starting the app and migrating the app....>


services: 
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
#   command: ./wait-for <databasenameOnHost>:<port> &&migrate-mongo up && npm start
#   command: ./wait-for db:27017 && migrate-mongo up && npm start



# .....
- db = name of computer or host or container name
- port = to receive trafic 


# A shorter way to write this ... is to create <an 'entrypoint 'script >

# docker-entrypoint.sh
echo "Waiting for MongoDB to start..."
./wait-for db:27017 

echo "Migrating the databse..."
npm run db:up 

echo "Starting the server..."
npm start 



# Dockerfile 

services:
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
#   command: "./docker-entrypoint.sh"



- # try to see if it works ... 

- bring down the project 

> docker-compose down 

- This does not delete the volume 

> docker volume ls 

- Delete the volume holding the project ...

> docker volume rm vidly_vidly

- Now the mongodb database is gone ... 

# Now restart the application ... 

> docker-compose up

- Now we get a database already populated with movies ... 

http://localhost:3001/api/movies/