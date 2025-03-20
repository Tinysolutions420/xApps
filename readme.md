DOCKER COMMANDS 

virtualization:
The process of running multiple os's parallely on single pice of hardware(OR)infrastructure(OR)hypervisor.
here we have hardware/infrastrucure (bare metal) on top of which we have host os ,on host os's we install an application called as hypervisor,
on the hypervisor we can run multiple operating system as guest operating system.

advantages:
1)Resource Optimization: Virtualization enables better utilization of hardware resources by allowing multiple virtual machines (VMs) to run on a single physical server. 
This consolidation reduces the need for additional hardware, leading to cost savings and improved efficiency.
2)Isolation: Each virtual machine operates independently of others, providing isolation and security. If one VM encounters an issue or is compromised,
 it doesn't affect other VMs on the same host.
3)Flexibility and Scalability: Virtualization makes it easier to scale resources up or down as needed. Administrators can allocate more CPU, memory,
 or storage to a VM without affecting others, providing flexibility to adapt to changing workloads.
4)Disaster Recovery and High Availability: Virtualization facilitates the creation of backup copies of VMs, making disaster recovery faster and more reliable. 
Additionally, technologies like VM migration and clustering enable high availability by automatically moving VMs to healthy hosts in case of hardware failure.
5)Testing and Development: Virtualization allows for the creation of isolated test environments, 
enabling developers to experiment with software configurations without impacting production systems. This reduces the risk of introducing bugs or instability into live environments.



hypervisor:
allows user to build multiple versions of complete operating system.

host os:
share the kernal with other container/system running as isolated process in user space on the host operating system.

containarization:
the process running on linux server is known as containarization.
this help developers to deploy multiple application using the some operating system on single vitual michine or server.
here we have hardware/infrastructure on top of the hardware we can inastall a application called hypervisor ,
and on top of the hypervisor we can install guest os ,on gust os  we can install docker engine application ,
on docker egine we can run multiple applcation in the form of container


advantages:
1)flexible                     
2)light weight
3)inter changble 
4)scalable
5)portable
6)fast deployment

these container pass througth less no.of layers to access the h/w resource.
and also organization no need to spend money on purchassing licenses on different os.

docker engine:
docker engine is open source containerzation technology for bulding and containerizing your applications
docker engine is core product of docker.

docker meachine :
docker meachine is a tool that lets you install Docker engine on the virtual hosts.

docker:
docker is a open-source containarization plaform for deploying,developing,and managing applications in light weight virtual environment
docker is a containarization platform or technology which packes your application and all it dependencies together in the form of container.
using docker we can create docker images.
advantages:
1)flexible                     
2)light weight
3)inter changble 
4)scalable
5)portable
6)fast deployment



docker container:
docker container is runable instance of an image ,you can stop,start,move, or delete it.
docker cnatiner,warp peice of software in complete file system that contains every thing to run: code,runtime ,system tools,any thing that can installed on server.
docker container consist of applications and all its dependencies ,but share the kernel with other container running as isolate process in user space on the host operating system.
A running instance of image is called as container.



docker image:
docker image is a file used to execute code in docker container.                 
docker image is source of docker container.
docker image is combination of bins/libs that are necessary for s/w applicaton to work.
instally all the softwares of docker are avalible in the form of docker images.
docker images are stored in the docker registory.
docker image does'nt have any state,and its state never changes it is just set of files.



Docker Architecture:
docker fllows client-server architecture,which include the main components that are docker client ,docker6 - host ,docker registory.
docker host :
 the server where docker is installed is known as docker hosts.
docker registory:
  docker registory is cloud site of docker where docker images are stored.+
    types of docker registory:
		1) public registory -> is called docker hub
		2)private registory ->it is used to share images within the enterprise.
docker hub:
   docker hub is cloud based registory service provided by docker for share our images with our team.
docker client:
  docker client is the command line interface(CLI) of docker where user can exectue docker commands.
  the docker client accepts these command and passes them to background process called "docker demon"
docker demon:
    these proccess accepts the command from the docker client and route the to work on docker image or conatiner
    or the docker registory.

=================================================================
docker instalion
-> Loging into AWS account

-> Create Linux Virtual Machine using Amazon Linux AMI

-> Connect to Linux VM using MobaXterm or putty or git bash

->goto to superuser terminal and install docker
   sudo -i   or  sudo su -

-> Execute below commands to install Docker s/w

$ sudo yum update -y
$ sudo yum install docker -y
$ sudo service docker start
to see detail information of docker version
docker version



================================================================================================================================================
Important commands of docker:


to see system details 
  docker system prune or info or events or df
   df: disk free usage
   event: to check the events like start stop pause etc..
    prune: delete the image or container
   info : details of system
working on docker images:
 
1) to pull docker images from registory(docker hub/ECR)
    docker pull image_name
2) to search docker images
   docker serach docker_images
3)to upload docker images into registory(docker hub/ECR)
    docker push image_name
4)to see the list of docker images that are download
   docker images
    or 
   docker image ls

   -deto get compelte deletails of image+9  
    docker images --no-trunc

5)to see detail info about docker images
    docker image inspect image_name/image_id
6)to delete docker image that is not linked to any container
    docker rmi image_name/image_id
       or
    docker image rm image_name/image_id

7)to delete docker image that is linked to any container
     docker rmi -f image_name/image_id
        or 
	docker image rm -f image_name/image_id
8)To save docker images as tar file   tar file menece zip file
   docker save image_name/image_d
9)to untar the docker image
    docker untar image_name/image_id
10) to delete all running and stoped images
     docker system prune -af
11)to see the history of images
      docker image history image_name/iname_id
12) to delete the unused images and no tag images and also known  as dangling
     docker image prune -af
13)to filter the docker images 
   docker images --filter "lable=nginx"    if there is multiple images
   docker images --filter "dangling=true"           (dangling meance unused images)
14)to delete multiple dangling images at a time
     docker rmi $(docker images -f "dangling=true" -q)

======
15)to create docker image from docker file
     docker bulid -t Image_name/Image_id .    # dot(.) is current working directory
16)to create docker image from docker file with name
   docker build -t Image_name/Image_id -f <custom name> .
17 to create docker image from the customised container
     docker commit container_name/container_id  image_name
=====
to work on docker container
======
1)to see the list of running docker container
    docker container ls
       or
	docker ps
2) to see the list of running and stoped docker container
    docker ps -a
3) to start the docker container
     docker start conatiner_name/container_id
4) to stop the docker container
     docker stop container_name/container_id
5)to kill the docker container 
  docker kill container_name/container_id
 
difference between docker kill and docker stop
  docker stop: the stop command allows the container to terminate gracefully
  docker kill: the kill command terminates it immediately.
5)to restart the docker container
      docker restart container_name/container_id
6) to restart after 10 seconds docker container
      docker restart -t 10 conatiner_name/container_id
7) to pause the container
   docker pause container_id/container_name
8)to unpause the container
   docker unpause container_name/container_id
7)to delete the running container 
   docker rm -f conatiner_name/conatiner_id
8)to stop all running container
   docker stop $(docker ps -aq)
9)to delete all stoped conatiner
     docker rm $(docker ps -aq)
   or 
    docker container prune
10)to delete all stoped and running container
     docker rm -f $(docker ps -aq)
11)to get detail info about container
   docker inspect conatiner_name/container_id
12)to see the logs genetrated by the container
   docker logs conatiner_name/container_id
12)to continue logs genetated  by the container
  docker logs -f container_name/container_id             -f : continuous logs your details
13)to create docker container
    docker run image_name/image_id
   run command options:
    --name: used to give name to the container
    --restart: used to keep container in running conditon
    -d: used to run container in deatched mode
    -it : used to open ineractive terminal to your container
    -e; used pass the environment variables
     -v: used to attach external device or folder as volume
     --volume-from: used to share volume with other container
    -p: used for port maping
         ex: -p 8000:80,
              8000:external port
              80: internal port
    -P: used for automatic port maping
    --link: used create link between multiple containers to create micro services architecture
    --network: used start container on specific network
    -rm : used to delete the container on exit
    -m: used for memory allocation of the container
    -c: used for cpu allocation for the container
     -ip:used to assign specific ip to container
    --hostname: in the ineractive terminal hostname will appre
13)to see the all details of the container in useage of memory cpc etc..
    docker stats container_name/container_id
14) to rename the container
  step1:stop the container 
        docker stop container_name
  step2: rename the container
        docker renmae container_name new_container_name
      ex:
        docker rename server sri
  step:3  start the container
      docker start container_id


14)to see the port used by the container `
    docker ports conatiner_name/container_id
15)to run process in container from outside the container
   docker exec -it container_name/container_id process_nmae          exec meance run command on running container
   example:  docker exce -it nginx bash
16) to come out from the container without exit
    ctrl+p,ctrl+q
17)to go back into a container from where the interactive terminal is running
    docker attach container_id/container_name
18)to see the process running in a container
   docker container conatiner_id/container_name top
19)to see the all details of the container in usage of memory cpc etc..
    docker stats container_name/container_id
20)to copy files from local or linux to container
    docker cp <current location>  <destnation location>
   example:
         docker cp ./script.sh server:/opt     server:container name

  and also u can copy files from container to local machine
    docker cp container_id:/opt/abc  .
21)to see details of docker engine
  docker info

commands on docker volumes:
1)to see the list of docker volumes
 docker volume ls
2)to create a docker volume
  docker volume create volume_name
3)to get detail info about the docker volume
 docker volume inspect volume_name/volume_id
4)to delete the volume
docker volume rm volume_name/volume_id


to setup microservice architecture.
1)using --link run command option
    this is used to create link between multiple container to set up micro service architecture.
2)docker compose:
  docker compse is a tool that was developed to help define and share multicontainer architecture.
  docker compse uses yml or yamal file to write the data.
  docker compose use yml file to setup micro service architeture and those files can be reused multiple times.

# Stop & remove the containers created by docker compose
$ docker-compose down

 docker compose installtion:
       sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/local/bin/docker-compose

       sudo chmod +x /usr/local/bin/docker-compose

       docker-compose version

  if there is different file name this is the command is used.
   docker-compose -f abcd.yml up -d
To delete the containers with coustom name
docker-compose -f lamp.yml down

to start the docker container
docker-compose start
to stop the docker container creted my docker compose
docker-compose stop


example1 with one network:
version:3.8:  ->specifies the version of the docker compose format.
service: is a logical group of containers that works togather to provide a specific functionality. like:image,conatiner name, ports, networks, volume any thing can be.

   ---
version: '3.8'
services:
  mydb:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: srinath
  apache:
    image: httpd
    ports:
      - 7800:80
    links:
      - mydb:srin
networks:
  default:
    external:
      name: sri
...
~


example 2:
 run container on different networking,create networking from compose
---
version : '3.8'
services:       version:3.8:  ->specifies the version of the docker compose format.
  jenkins:
    image: myjenkins/jenkins
    ports:
      - 7900:8080

    networks:
      - srinath
  qaserver:
    image: tomee
    ports:
      - 6060:8080
    networks:
      - sri
  prodser:
    image: tomee
    ports:
      - 7070:8080
    networks:
      srinath1
networks:
  srinath: {}
  sri : {}
  srinath1: {}
...
  




docker volume:
   docker containers are stateless.
  containers are tempory or ephemeral but the data produced by the containers should be preseved or persisent or perminent.
  once the container is deleted data prouced by the container is lost,
   we to preserve the data even if the container is deleted ,we can use volumes
mounting types:
  1)tmps
  2)docker volume
  3)bind mount(simple and sharable)
 volumes are three types:
  1)simple docker volume
  2)sharable docker volume
  3)docker volume container

 
   simple docker volume:
            these volume is used only for preserving the data on the host machine even if the container is deleted.
         
         
        
   sharable docker volume:
		the volumes are sharable between multiple container
           
   docker volume : 
       docker volume are bidirectional ,if the changes done on the host meachine will be reflected to container,if changes done on  the container will be reflected to host machine. 

Q) What is Dangling volume in Docker ?

-> The volumes which are created but not associated to any container are called as Dangling Volumes

vim dockrer.yml
---
version: '3.8'
services:
  myvol:
    image: nginx
    ports:
      - 9000:80
    volumes:
      - /var/lib/docker/volumes/sri/_data:/usr/share/nginx/html/

volumes:
  sri:
    external: true
...

docker file:
     dockerfile is predefined keyword to create customised docker images.
     dockerfile will use DSL(domain specific language) keyword
  Important keyword in docker file:
FROM
MAINTAINER
COPY
ADD
RUN
CMD
ENTRYPOINT
ENV
LABEL
WORKDIR
USER
EXPOSE
VOLUME
ARG

FROM  :

This is used to specify the base image for where a customised docker images has to be created
 
syntax: 
  FROM java:jdk-1.8
  FROM tomcat:9.5
  FROM mysql:6.8
  FROM python:3.3

MAINTAINER:
  this represents the name of the organization (OR) the author who is cretaed this file.
   
syntax: 
MAINTAINER  Ashok <ashok.b@oracle.com>
MAINTAINER  srinath
 
COPY:
copy command is used to copy the files,directories and remote url from host to customied docker image(source to destination )while creating docker image

Syntax:

COPY <source-location>  <destination-location>

Ex: 

COPY   index.html  /var/www/html


ADD:
ADD command is used to copy the files,directories and remote url from host to customied docker image(source to destination )while creating docker image
                                 or
Add command is similar to copy files,directories from host to coustomized docker image(source to destination),but add can 
also download files from some remote server.

Syntax:

ADD <source-location>  <destination-location>

ADD <url>  <destination-location>


Q) What is the difference between COPY and ADD commands ?

-> Using COPY command we can just copy the files from one path to another path with in the machine

-> Using ADD command we can copy files from one path to another path and it supports source location as URL also(zip,tar,bizip2).

RUN:
run command used to run linux or any  commands in the current image/container,generally it is used to do software installtion or running script

ex:
RUN yum install maven
RUN yum install git 
RUN git clone repo-url
RUN mvn clean package


CMD:
CMD is used to execute instruction while creating Container
CMd is used to execute commnd when container is creating or running
ex:
CMD  sudo start tomcat
CMD ["service", "httpd" "started"]

Q) What is the difference between RUN and CMD in Dockerfile ?

-> RUN is used to execute instructions while creating image
-> CMD is used to execute instruction while creating Container

-> We can write multiple RUN instructions in Dockerfile, docker will process all those instructions one by one.
-> If we write multiple CMD instructions in Dockerfile, docker willl process only last CMD instruction.

ENTERYPOINT:
  ENTRYPOINT instructions will execute while creating container
		or 
  ENTRYPOINT is used to execute instruction while creating Container
ENTRYPOINT is used to execute commnd when container is creating

Syntax
---------

ENTRYPOINT [ "echo"  , "Welcome to Ashok IT" ]

ENTRYPOINT [  "java" , "-jar" , "target/boot-app.jar"  ]

Q) What is the difference between CMD and ENTRYPOINT ?

-> We can override CMD instructions in runtime while creating container

-> We can't override ENTRYPOINT instructions

WORKDIR:
 used to specify the default working directory for image/container
ex:
WORKDIR  /app/

ENV:
ENV is used to set Environment Variables for your image
ENV is used to pass the envernoment variables for your image
ENV IS USED TO DEFINE RUN-TIME VARIABLES.

Ex:

ENV <key> <value>

USER:
 this is used to specify who should be the default user to login into the container

ex:
USER root

expose:
 expose used to specify the what port should be used by the container.
  it is not for public,it is used internally

ex:

expose 8080

publish: -p
  it will connect to the internet

LABEL:
label is used to store data about the docker image in key value pairs
ex:
LABEL "APP_ENV"="production"

volume:
 volume used for automatic volume mounting.
 we will have a volume mounting automatically when the container start.

ex:
VOLUME /MYVOL


ONBUILD:

ARG
====

is used to pass envernomental variables with key_values,but this variable will set only during the image building ,not on the container
ARG IS USED TO DEFINE BUILD-TIME VARIABLES.

DIFFERENCE BETWEEN ARG AND ENV.
ARG IS USED TO DEFINE BUILD-TIME VARIABLES.
ENV IS USED TO DEFINE RUN-TIME VARIABLES.

Ex:

ARG branch

RUN git clone -b $branch <repo-url>

$ docker build -t imageone --build-arg branch=master



cache busting :
 when we create an image from the docker file docker stores the information about you infrastructure in its cache.
  => next time if we edit the same docker file and add new few instructions  and build image ,out the docker will not execute the previously statement.
  => instead it will read them from the cache


examples for docker files:

ex1:
FROM httpd
MAINTAINER srinath
RUN apt update -y\
     &&  apt install -y git curl nginx net-tools\
     && apt install -y maven\
     && mkdir myapp \
     && apt-get install systemctl -y
EXPOSE  8900
WORKDIR /myapp
copy index.html /myapp
COPY myshel.sh /myapp
COPY index.html /var/www/html
CMD bash /myapp/myshel.sh



example 2:
FROM httpd
MAINTAINER srinath
RUN apt update -y\
     &&  apt install -y git curl nginx net-tools\
     && apt install -y maven\
     && mkdir myapp \
     && apt-get install systemctl -y
EXPOSE  8900
WORKDIR /myapp
copy index.html /myapp
COPY myshel.sh /myapp
COPY index.html /var/www/html
ENTRYPOINT bash /myapp/myshel.sh



example 3:

FROM ubuntu
MAINTAINER srinath
RUN apt update -y\
     &&  apt install -y git curl nginx net-tools\
     && apt install -y maven\
     && mkdir myapp\
     && apt install -y nginx vim
WORKDIR /myapp
COPY index.html /myapp
COPY myshel.sh /myapp
ADD https://github.com/mavrick202/terraformsingleinstance.git /myapp
EXPOSE  80 8080 8900
CMD bash service nginx start




example 4:


FROM httpd
MAINTAINER srinath
RUN apt update -y\
     &&  apt install -y git curl nginx net-tools\
     && apt install -y maven\
     && mkdir myapp \
    && apt install -y iputils-ping\
     && apt-get install -y vim\
     && apt-get install systemctl -y
EXPOSE  8900
WORKDIR /myapp
copy index.html /myapp
COPY myshel.sh /myapp
COPY index.html /var/www/html
#CMD ["service", "httpd" "started"]
#CMD  bash  /myapp/myshel.sh
ENTRYPOINT ping www.google.com


example 5:
  
FROM ubuntu
MAINTAINER srinath
RUN apt update -y\
     &&  apt install -y git curl nginx net-tools\
     && apt install -y maven
USER root
EXPOSE 9000

example 6:
FROM ubuntu
MAINTAINER srinath
RUN apt update -y\
     &&  apt install -y git curl nginx net-tools\
     && apt install -y maven
RUN useradd srinath
USER srinath
EXPOSE 9000


Docker Networking:

The Docker network is a virtual network created by Docker to enable communication between Docker containers.
If two containers are running on the same host they can communicate with each other without the need for ports to be exposed to the host machine.
There are several network drivers available in Docker.


default networks are:
  1)none or null
  2)host
  3)bridge
network drivers:
   1)bridge
   2)null
  3)host
  4)overlay

bridge network: bridge network is default network is created automatically,when you start docker.
             by default container are running on default bridge network.
user define bridge network:
we can create over network,by giving our own ip appdress
by cretaing over own bridge netork we can assign that network to on catainer or more container.

    docker0 is a default bridge network(172.17.0.1)
    eth0: is ec2 server ip address 

host network :
 host network is standalone for container,it remove the isolation between docker container and docker host,uses the hosts network directly.
 ip address will not assigned to container.

 
none:
none network means no network provided to your docker containers.
 


docker network commands:
1)to see the list of docker networks
  docker network ls
2)to create docker network 
 docker network create --driver network_type network_name
3)to get detailed info about a network
 docker network inspect network_name/network_id
4)to delete the docker network 
   docker network rm network_name/network_id
5)to connect a ruuning container to a network
 docker network connect network_name/network_id   container_name/container_id
6)to disconnect a running container to a network
 docker network disconnect network_name/network_id   container_name/container_id
7)to give subnet to the docker network 
 docker network create --driver driver_name --subnet subnet_id network_name
  ex:
   docker network create --driver bridge --subnet 172.8.0.0/16 srinath_pod
another command for gateway:
 docker network create --driver driver_name --subnet subnetid --gatway gatewayid network_name
 ex:
   docker network create --driver bridge --subnet 172.8.0.0/16 --gateway 172.8.0.1 srinath_pod



docker hub:
docker hub is cloud based registory service provided by docker for share our images with over team members.
1)public repository

2)private repository

example for pushing image to docker hub and the porject 1:

create index.html in the current working folder
vim index.html
<!DOCTYPE html>
<html lang="en">
<head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <link rel="stylesheet" href="style.css">
        <title>Color Game</title>
</head>
<body>
        <h1>The Greatest World welcome srinath k<span id="rgb">RGB</span> Color                                  Game</h1>
        <h1> hai devopd</h1>
        <div id="smallcont">
                <div></div>
                <div id="try1">Lets Play</div>
        </div>
        <div id="container">
                <div class="square"></div>
                <div class="square"></div>
                <div class="square"></div>
                <div class="square"></div>
                <div class="square"></div>
                <div class="square"></div>
        </div>

</body>
<script type="text/javascript" src="scorekeeper.js"></script>
</html>


create a docker file

vim dockerapache2

FROM ubuntu

RUN apt-get update -y\
    && apt-get install -y apache2

COPY index.html /var/www/html/

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]

now build docker image from docker file with tags
 docker build -f dockerapache2 -t srinathkoraboina/apache:h1 .
check the docker image is running or not
  docker run --name srinathk -it -d -p 8900:80 IMAGEID
 if container is not running on the port number time this command
  docker run -t -i -p 8100:80 fbb16b27024a /bin/bash        fbb16b27024a->>image id


after checking the docker image,docker images running imeance push the image into docker hub

step1:type login command in CLI(command line inetface)
 docker login
  username;srinathkoraboina
  password: srinath koraboina
 step2: push docker image to docker hub
 docker push IMAGE_NAME/IMAGE_ID


project2:


FROM httpd
MAINTAINER srinath
RUN apt update -y\
     &&  apt install -y git curl nginx net-tools\
     && apt install -y maven\
     && mkdir myapp\
     && apt install -y nginx vim\
     && apt install wget -y
WORKDIR /myapp
COPY index.html /usr/share/nginx/html/
#ADD https://github.com/mavrick202/terraformsingleinstance.git /myapp
EXPOSE  80 8080 8900
CMD /usr/sbin/nginx -g "daemon off;"


project 3 python application:

vim Dockerfile

FROM python:alpine3.10
WORKDIR /app
COPY . /app
#RUN apt update -y\
 #   apt install -y python\
 #  apt install -y net-tools
RUN pip install -r requirements.txt
EXPOSE 5000
CMD python ./launch.py

create on python application
vim launch.py

from flask import Flask
helloworld = Flask(__name__)
@hellowold.route("/")
def run():
    return "welcome to python.."
if __name__ == "__main__":
    helloworld.run(host="0.0.0.0",port=int("5000"), debug=True)

create a requirements.txt
vim requirements.txt
flask




project 4 with nodejs:

FROM node:19.5.0-alpine

WORKDIR /usr/app

COPY ./ /usr/app

RUN npm install

CMD ["npm", "start"]


create a index.js
index.js

const express = require('express');

const app = express();

app.get(\%, (req, res) =>\

res.send('WELCOME TO NODEJS...);

});

app.listen(8080, 0 =>\

console.log('Listening on port 8080'); });



create package.json

{
        "dependencies":{
                "express": "*"
        },
        "scripts": {
                "start": "node index.js"
        }
}



name space:
to provide the isolated workspace container.few name spaces types supported by docker is pid,mount,ipc,user,network

Docker SWARM:
Docker Swarm : It is an Orchestration Platform. It is used to manage docker containers.

-> Managing docker containers nothing but creating / updating / scale up / scale down / remove containers


Note: In market we have docker swarm, kubernetes, open shift,Amazon ECS as Orachestration platforms.

Docker Swarm is used to setup Docker Cluster

-> Cluster means group of servers

-> Docker swarm is embedded in Docker engine ( No need to install Docker Swarm Seperatley )

-> We will setup Master and Worker nodes using Docker Swarm cluster

-> Master Node will schedule the tasks (containers) and manage the nodes and node failures

-> Worker nodes will perform the action (containers will run here) based on master node instructions


 Enable 2377 port in security group for Swarm Cluster Communications

====================
Docker Swarm Service
====================

-> Service is collection of one or more containers of some image

-> There are 2 types of services in docker swarm

1) Replica (default mode)
2) global


replica:
  replicas 
  


docker realtime challanges:
1)docker is a single demon process. which cause a single point of failure,If if docker demon goes down for some reason all the applications are down.
2)resource constraints: if your are running too many containers on a single host, you may experience issues with resource constraints.this can result in slow performance or crashes.
