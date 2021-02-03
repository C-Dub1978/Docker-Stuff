FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80/tcp

# This is for anonymous volumes which are kind of pointless
# If you need to persist data, used named volumes in run command or set up a
# bind mount
VOLUME ["/app/feedback"]

CMD ["node", "server.js"]