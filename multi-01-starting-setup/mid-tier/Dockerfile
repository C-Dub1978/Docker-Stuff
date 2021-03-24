FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80/tcp

CMD ["node", "app.js"]