# docker-cli
All CLIs about docker

How to remove all docker images stored in a local repository

The following commands can be used to remove all Docker images stored in your local repository. Be aware that you would not be able to undo any of the removed docker images. First, list all your docker images to make sure that there is nothing you want to remove:
# docker images
Using the following command you can obtain image IDs of all your docker images:
# docker images -q
To remove a single docker image simply run docker rmi followed by the image ID. For example:
# docker rmi 9fa0e1f381ad
In order to remove all image at once with a single command we can combine two commands together:
# docker rmi `docker images -q`
The above command will not remove images which are currently being used by containers and the following error message will appear:
Error response from daemon: Conflict, cannot force delete 568f5ffe3905 
because the running container 9fa0e1f381ad is using it, stop it and retry
To remove docker images even if they are used by container use force switch:
# docker rmi -f `docker images -q`
