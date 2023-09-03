FROM node:14-alpine

WORKDIR /app

# CMD npm init
#? We don't want torestrict this image to just being able to execute npm init command.
#? We want to give the user full control over this image and allow the user to run any command against this image.
#? So we did not use CMD command.


## Utility container ##
# We can use utility container to execute something which has effect on the host machine
# without having to install all the extra tools on the host machine => Bind mount

# By using bind mount, we are sharing our host machine folder with the folder inside of the container
# and the commands which we execute inside of the container inside of this shared folder.
# Therefore, they also have an effect on our host machine.


ENTRYPOINT [ "npm" ] 
# If we add a command after the image name on docker run, the stating command overwrites the command secified in a Dockerfile
# Ex: docker run -it --rm -v $(pwd):/app node:14-alpine npm init, here npm init will over ride CMD in the dockerfile

#? ENTRYPOINT is like CMD, the difference is the added command will be appended to the command specified in ENTRYPOINT