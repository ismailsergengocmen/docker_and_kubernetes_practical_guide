# Allow building image up on another base image
#? Basically telling I will start with node image, in my own image
FROM node:12

# Set the working directory
#? All the subsequent commands will be executed relative to this path
WORKDIR /app

COPY package.json /app

# This will run when the image is built
RUN npm install

# Which files that live on our local machine, should go into the image
#? First path is to path that specify where the file is on our local machine outside the image
#* The . means that outher files in the same file that contains the Dockerfile
#? Second path is to path that specify where the file should be in the image
#* It is best to not to use root file
COPY . /app

# This port will exposed to the local system so that if there is a server listen to this port, it will be accessible
# ? This command is just for documentation purposes, to show port mappings. It does not actually do anything
EXPOSE 80

# Tell the image what to do when it starts as a container
CMD ["node" , "server.js"]

# Images are locked and finished once we built them. 
# Everything in images is read only then and can't edited from the outside by simply updating our code.
# We need to rebuilt an image if we want to change something in it

# Images are layer based. Every instruction represents a layer in the Dockerfile
# Docker caches every instruction result and when we rebuild the image it will used the cached result if there is no need to run an instruction again
# If any instruction result chaned, every instruction after that is not used from cache.

# docker run creates a new container from the image and runs it
# If nothing changed about the application, we can just restart and existing container
# using docker start <container id/name>


## RUN VS START VS CREATE ##
# docker create = create a new container
# docker start = start an existing container
# docker run = docker create + docker start

# In starting with docker start, the detached mode is enabled by default
# In running with docker run, the attached mode is enabled by default 
#? In attached mode, we can see the output of the container in the terminal because it runs on foreground
#? In detached mode, we can't see the output of the container in the terminal because it runs on background
#* One can use docker start -a <container id/name> to start it as attached mode

#! Yet, we can use docker logs to see past logs of a container. Also by using -f we can attach a detached container to see its logs