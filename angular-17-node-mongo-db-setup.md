## Prompts

I set it up with these two prompts using Cloud Code. 

```bash
Can you checkout and start the server and client of this project locally ?
https://github.com/bezkoder/angular-17-node-project/blob/master/README.md

User answered Claude's questions: Which database backend would you like to use for the server? 
> Answer → I do not have any of them, could you help me set up a docker container
with a MongoDB database so we can use the 1st option?
```

## Commands

```bash
git clone https://github.com/bezkoder/angular-17-node-project.git .../angular-17-node-project
docker run -d --name mongodb-bezkoder -p 27017:27017 mongo:latest
# Now let me install and start the Node.js server
cd .../angular-17-node-project/node-express-mongodb-server && npm install
 # The Node.js server is running on port 8080 and connected to MongoDB
 #  Now let me set up the Angular client
 cd .../angular-17-client && npx ng serve --port 8081

```

## Setup

```bash
Project Setup Complete

  MongoDB Database:
  - Running in Docker container mongodb-bezkoder on port 27017

  Node.js Backend Server:
  - Running on http://localhost:8080
  - Connected to MongoDB successfully

  Angular 17 Frontend Client:
  - Running on http://localhost:8081

  You can now open your browser and navigate to http://localhost:8081 to use the Tutorial application. The app allows you to:
  - Create, read, update, and delete tutorials
  - Search tutorials by title
  - Mark tutorials as published/unpublished

  Useful commands for later:

  # Stop MongoDB container
  docker stop mongodb-bezkoder

  # Start MongoDB container again
  docker start mongodb-bezkoder

  # Remove MongoDB container
  docker rm mongodb-bezkoder

```