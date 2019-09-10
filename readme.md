## Launch a dokcer container with support for GDB and mount a docker volume 

`docker run --cap-add=SYS_PTRACE --security-opt seccomp=unconfined --rm --name wcont -it -v workdir:/home -w /home linuxdevenv:18.04 /bin/bash`
* linuxdevenv:18.04 is the docker image, workdir is the dokcer volume
* upon launch this will provide a shell, the -it option is required to launch a shell

## Managing files between host and container 
#### create a docker volume named *workdir*
`docker volume create workdir`
#### copy files to docker volume from host directory
1. A docker conatiner is necessary to copy files into the docker-volume named *workdir*

2. Start a dummy container to facilitate copying `docker run -d --rm --name dummy -v workdir:/home ubuntu tail -f /dev/null`

3. Copy all files from host directory *dirname* into docker-volume *workdir* `docker cp c:\dirname\* dummy:/home/*`

4. Stop the container `docker stop dummy`

#### copy files to host directory from docker-volume
* `docker cp dummy:/home/* c:\dirname\`

## Saving and exporting to transfer images 
#### saving a docker image in tar format 
docker save --output="output.tar" image_name

#### exporting a docker container in tar format 
docker export --output="output.tar" container_id
