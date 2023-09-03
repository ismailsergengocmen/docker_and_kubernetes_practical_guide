FROM node:15

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

CMD ["node", "app.js"]

#* If an app tries to connect or send a request in another local server and it will be dockerized,
#* the localhost should be changed to host.docker.internal. Because localhost actually points
#* some other service inside of the container. host.docker.internal translated to real local host
#* IP by Docker