FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 3000

# This only starts a development server for React code
CMD ["npm", "start"]

#* React code is not executed inside of the container, it runs on browser
#* Browser has no idea where the API request should be sent
#* Currently its like const reponse = await fetch("http://goals-backend/api/persons")
#* Therefore using container name in the API requests is not an option

