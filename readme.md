#### Create a docker volume named *workdir*
`docker volume create workdir`
## Copy files to docker volume from host directory
*A docker conatiner is necessary to to copy files into the docker-volume named *workdir*

..* Start a dummy container to facilitate copying `docker run -d --rm --name dummy -v workdir:/home ubuntu tail -f /dev/null`

..* Copy all files in *dirname* directory into docker-volume *workdir* 'docker cp c:\dirname\* workdir:/home/*'

..* Stop the container docker stop dummy

