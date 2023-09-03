FROM python

WORKDIR /app

COPY . /app

CMD ["python", "rng.py"]

## BUILD VS CREATE
# docker build creates a new image from the base image and the Dockerfile
# docker create creates a new container from the created image

#* By combining -it we'll get a terminal exposed by the container to get input from user
#* or if you want to use create + start combination you can use -ai to attach the container
#* and add a terminal to it
#Ex: docker build . => builds the image from the Dockerfile in the current directory, dot means Dockerfile will be in the same folder

## SEE IMAGES & CONTAINERS ##
# docker ps lists containers
# docker images lists images

## DELETE IMAGES & CONTAINERS ##
# docker rm <container_id>
# docker rmi <image_id> <image_id> <image_id>
#* When you delete an image you see all deleted layers of the image. For example let's say you use node base image
#* It also builds on top of another image like linux OS. That's the reason you see many several image
#* deletion when you delete a single image

#! An image can only be deleted if there are no containers uses that image. Hence, you need to delete related container first.

# docker image prune deletes all unused images
# -a can be used to remove every image. docker image prune -a removes all images

## REMOVING STOPPED CONTAINERS AUTOMATİCALLY ##
#* --rm flag removes the container when it's stopped automatically
#? This flag is useful if you have a server which stops only for code changes. Since the new container need
#? to be recreated after every code change.

## INSPECT ##
# docker inspect <container_id> gives you detailed information about the container

## COPYING FILES INTO & FROM A CONTAINER ##
# To sent file => docker cp <file_name>/<file_path> <container_id>:<path which files sent in container>
# To get file => docker cp <container_id>:<file_path> <file_name>/<file_path>
#? Useful to add file(such as conf. files for server) without rebuilding the image or restarting the container

## NAMING & TAGGING ##
# --name flag is used to give a name to the container
# -t option is used to give a tag to the image
#Ex: docker build -t <docker_name>:<tag_name> => creates an image with given name and tag combination

## SHARE IMAGES ##
# docker push <image_name> pushes the image to the docker hub
# docker pull <image_name> pulls the image from the docker hub
#Ex: docker pull <docker_name>:<tag_name> 
#! docker pull pulls the latests version of given image. Also if docker run can not find an image locally
#! it will check the container history, in this case DockerHub to find the image

#tag command can be used to tag an existing image
#Ex: docker tag <current_image_name>:<current_tag_name> <new_image_name>:<new_tag_name>

#! When an image is renamed, you did not get rid of old image. Instead a clone is created for old image.
#? To upload an image to Docker Hub, user should have logged in from terminal using docker login command
#? Then, the image should be renamed according to the given repository name from docker hub which is
#? determined by the user when creating the repository