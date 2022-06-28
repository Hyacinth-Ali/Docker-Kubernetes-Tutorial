FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

ENV DATABASE_URL=localhost

CMD ["node", "app.js"]