#### create a docker volume named *workdir*
`docker volume create workdir`
#### copy files to docker volume from host directory
1. A docker conatiner is necessary to to copy files into the docker-volume named *workdir*

2. Start a dummy container to facilitate copying `docker run -d --rm --name dummy -v workdir:/home ubuntu tail -f /dev/null`

3. Copy all files in *dirname* directory into docker-volume *workdir* `docker cp c:\dirname\* dummy:/home/*`

4. Stop the container `docker stop dummy`

#### copy files to host directory from docker-volume
* `docker cp dummy:/home/* c:\dirname\`

#### exporting a docker image in tar format 
docker export --output="output.tar" image_name

#### exporting a docker container in tar format 
docker export --output="output.tar" container_id
