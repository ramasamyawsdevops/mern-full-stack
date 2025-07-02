# docker run -it -d --name mongo -p 27017:27017 mongo

------------------------

# git clone https://github.com/ramasamyawsdevops/mern-full-stack.git

cd backend/

# docker build -t backendimg:v1 .

# cat .env

MONGO_DB_URL=mongodb://mongo:27017/traineesDB
PORT=5000

*********************************

# docker run -it -d --name backencon --link mongo -p 5000:5000 backendimg:v1

-----------------------


# docker exec -it mongo /bin/bash

# mongosh

---------------------

### Dockerfile of backend

# cat Dockerfile

FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install
COPY . .

ENV PORT=5000
ENV MONGO_URI=mongodb://mongo:27017/traineesDB

EXPOSE 5000

RUN npm install -g nodemon
CMD ["nodemon", "index.js"]

******************************


# cat db.js

const mongoose = require('mongoose');
require('dotenv').config();

const connectToMongoDB = () => {
    try {
        mongoose.connect(process.env.MONGO_DB_URL);
        console.log("Connected to MongoDB Successfully!!");
    } catch (e) {
        console.log(e.message);
    }
}

module.exports = { connectToMongoDB };


docker build -t backendimg:v1 .

docker run -it -d --name backentcon --link mongo -p 5000:5000 backendimg:v1

cd ..
cd frontend/

### Dockerfile of frontend

# cat Dockerfile


FROM node:18-alpine as build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build


FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

******************

# docker build -t frontendimg:v1 .
# docker run -it -d --name backcon -p 8081:80 frontendimg:v1


 axios.delete('http://65.0.135.226:5000/v1/api/trainees/deleteTrainee', 


change the ip address
