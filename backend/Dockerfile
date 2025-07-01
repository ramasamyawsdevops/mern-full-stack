FROM node:18

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

ENV PORT=5000
ENV MONGO_URI=mongodb://mongo:27017/traineesDB

EXPOSE 5000

CMD ["nodemon", "index.js"]
