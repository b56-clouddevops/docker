# docker


### Challenges with servers 

1) Each and every applicaition is highly dependent on the Underlying OS.
2) One VM cannot share the under-utilized resources with the neighbour VM's.
3) Configuration Management [ If app-a works on VM-a, there is no guarantee that app-a works on VM-b ]

Container : This a package with your Application + Pre-requisties + Libraries.
            This package is the container or our artifact.
            If this works on your linux machine, that shoudl any where.

To run container, what should I install ?

    1) You need to have a linux machine.
    2) Install Container Run Time. 
    3) You're good to run your containers.


### Container vs Docker 

    * Container is a package of your application.
    * Docker is a container run-time to run the containers on linux machine. 

# docker notes

### Docker is a container run time.
```
Docker gives us high-level runtime as it uses CONTAINERD as its run-time.
```

### What is a container ?
```
Container is a package of software that contains all the required elements to run your applicaition in any environment
```

### What is Run Time ?

```
To run containers, you need to have a run time and among all, DOCKER is highly used
```

### How to run a container ?

```
$ docker run containerName    ( this runs containers interactively killing your prompt )
$ docker run -d containerName ( this runs containers in the background by detaching from the terminal )
```

### Common docker commands:

```
$ docker ps                          ( shows you the list of all the running containers on your system )
$ docker ps -a                       ( shows you the list of all the containers including the exited ) 
$ docker pull imageName              ( pulls the docker image from the image repository )
$ docker push imageName              ( pushes the docker image to the image repository )
$ docker stop                        ( To stop the container which is running ) 
$ docker exec -it containerName bash ( To enter in to the container )
```

### How a docker container looks like ???

```
* docker.io/docker.io/imageName:version 
(repoName)(uesrName)

--> Examples of repoNames:  docker.io , ecr.io , gcr.io

```


### Volume Mapping :

```
Mounint the local linux directory on the containers directory to achieve directory persistance
```

### Port-Forwarding:

```
$ docker run -p 80:80  -d  nginx

```
### Dynamic Porting:
```
docker run -P  -d httpd
```
### Volume Mapping 

```
docker run -v /home/verma/mysql-data:/var/lib/mysql  -e MYSQL_ROOT_PASSWORD=password -d mysql
```

 ### Dockerfile reference :
 ```
 https://docs.docker.com/engine/reference/builder/
 
 ```

### ENTRYPOINT vs CMD

```
 The ENTRYPOINT specifies a command that will always be executed when the container starts. The CMD specifies arguments that will be fed to the ENTRYPOINT.
```

### Both CMD and ENTRYPOINT instructions define what command gets executed when running a container. There are few rules that describe their co-operation.

* Dockerfile should specify at least one of CMD or ENTRYPOINT commands.
* ENTRYPOINT should be defined when using the container as an executable.
* CMD should be used as a way of defining default arguments for an ENTRYPOINT command or for executing an ad-hoc command in a container.
* CMD will be overridden when running the container with alternative arguments.


### How to tag an imageName during build ?

docker build -t docker.io/sanraman/cart:v1 .  

### How to tag an existing image ?

docker tag docker.io/sanraman/cart:v1 imageID 


### What are few of the best practices of DOCKER IMAGING

```
    * Size of the Docker Image has to be as minimal as possible 
    * Securiy of the Images , it should zero to none vulnerabilites as per your organization standard

```


### Important Point :

```
1) Stopping the container means KILLING the container 
2) Starting the container means CREATING a new container
```