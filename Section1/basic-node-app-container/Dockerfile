 FROM node:14 

 WORKDIR /app

 COPY package*.json /app

 RUN npm install

 COPY . .

 ENV PORT 3000

 EXPOSE $PORT
 
 CMD [ "node", "app.js" ]