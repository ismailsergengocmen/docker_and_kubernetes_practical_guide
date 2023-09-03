FROM node:14

# We can set default values for environment variables with ARG command
#* We can override these values when we run this container
#* This arg can be used on all the other commands
#! Since this instruction also adds a layer, any subsequent instruction will be rexecuted when this arg changes
#Ex: docker build -t <image-name> --build-arg <arg-name>=<arg-value> 
ARG DEFAULT_PORT=80

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

# We can set environment variables with ENV command
#* We can configure env variables when we run this container
#* --env-file flag can be used to set env variables from a .env file
#Ex: docker run -p <ports> --env-file <relative-file-path> <image-name>
ENV PORT $DEFAULT_PORT

EXPOSE $PORT

## Anonymous Volumes ##
# This path is in the container and mapped to some folder outside the container where the data should survive
#* This in an anonymous volume. If the related container stopped, the volume will be deleted
# They closely atteched to one specific container
#Ex: VOLUME [ "/app/feedback" ]

## Named Volumes ##
# Named volumes are great for data which should be persistent but which you don't need to edit directly
# Named volumes can not be created with dockerfiles, they have to be created when we run container using -v flag
#* They did not deleted when a container stopped
#? Perfect for persistent data but not editable
#Ex: docker run -p <ports> -v <volume-name>:<file-system-path> <image-name>

## Bind Mounts ##
# We set the path which the container internal path should be mapped on our host machine
# If we put our code to the bind mount, container would always access latest code instead of a snapshot
#? Perfect for persistent and editable data
#Ex: docker run -p <ports> -v <host-absolute-path>:<container-path> <image-name>

#! Docker will not overwrite local host folder determined with host-absolute-path, instead local host folder 
#! overwrites container folder. That's why when we tried to run the container, we got an error that says there is no express module
#* Using another volume for node_modules folder is a solution for this problem
#Ex: docker run -p <ports> -v <host-absolute-path>:<container-path> -v /app/node_modules <image-name>

#! We can not see bind mounts in volume list, since docker does not manage them
CMD ["npm", "start"]