### Getting started with Docker

#### Installing Docker

On Mac, run the following commands to install docker:
`brew install virtualbox docker docker-machine docker-compose boot2docker`

(Note that boot2docker is depreciated in favor of docker-machine, but is easier to use)

Setup an accout at hub.docker.com

Setup an AWS EC2 Container Service (ECS) account

#### Create a docker VM locally

To use the boot2docker command:

```
boot2docker init
boot2docker start
```

To use the docker-machine command (recommended)
```
docker-machine create -d virtualbox <machine name>
docker-machine start <machine name>
```

Run `docker-machine ls` to list the created machine and any others that
have been made.

To get the connection information for connection to machine:
`docker-machine env <machine name>`

Then setup your bash shell ENV to be able to connect to the machine:
`eval "$(docker-machine env <machine name>)"`
This runs the `export` commands printed out by the docker-machine command.

Run the following to confirm that docker is working:

`docker version` - list info for both client and server.
`docker ps` -  list the running docker processes

```
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
```

`docker run hello-world`

#### Create a docker image based on an application

As an example we will clone a repo from AWS ECS to build an image.

`git clone https://github.com/awslabs/ecs-demo-php-simple-app`

Create a repo at AWS ECS

`docker built -t <repo name> .`

`<repo name>` is the name of the AWS ECS repo that you just created.

`aws ecr get-login --region us-west-2`

run the docker login command returned by this command

`docker tag test:latest <your repo url>/test:latest`

`aws ecr `

look at the .json file in the demo app dir.

#### 

#### Deploy a client/server app in

##### Create seperate containers for the client and server

Our react client is served as a webpage when built (no need for node).  Therefore
we will use a standard webserver environment.  For this example I will
use the nginx web server.

###### The Client container

* Go to the client dir of your zootopia app.
* Run yarn build to create the static files for your react app.
* Create a Dockerfile:
```
FROM nginx:1.13.0

COPY build /usr/share/nginx/html
```
This is the simplist dockerfile for a nginx server

* `docker build -t <repo name> .`

###### The API server containers

*
*

```
```
