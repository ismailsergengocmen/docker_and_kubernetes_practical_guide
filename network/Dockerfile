FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

CMD ["node", "app.js"]

#* Sending requests from inside your container to WWW just works without any special settings.
#* host.docker.internal => Translated to the IP address of the host machine
#? You can use this to access a service running on the host machine from inside a container such as a local database client.
#* After the network is crated, we can use the name of the network to connect containers together.
#Ex: docker run --network <network-name> <image-name>

#* For API calls, when a network is created, we can use the name of containers to send requests
#Ex: fetch("http://<container-name>/api/persons")