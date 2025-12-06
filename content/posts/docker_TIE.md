---
draft: false
title: 'Docker Tutorials+Insights+Exp'
tags: ["Docker","Resources","Insightful"]
---

>**Note**: I am not going to say the same things that are said in the documentations but i am going to share what i learnt and understood about it along with insights and experiences as the tittle suggests and things that are related to the environment is based on `fedora 41` only because that's what i use :>

# Docker:-
Based on my understanding docker is used to solve one of the most important classic problem of the entire software community which is "It works on my computer without any errors but why doesn't it work in your's". But if you ask me "does docker became famous for just solving that one particular problem", I would say that it's kind of a very big problem that was solved by docker which made it cool but it's not the only problem it solves. Docker provides lot of other features which helps us seperate our code from the system thus enhancing security and efficiency and it also allows us to run multiple code at the same time but the cool part is each and every code runs on its own container without affecting each other. Let's say you are fond of developing stuffs but you just have one system and you want ot run multiple projects but here's the catch each project requires different versions of the same environment, now that's a problem right ofcourse i know you can run in `virtual environments(VENV)` if you are using `python` and `nvm` for `Nodejs` and `jEnv` for `java` and so on.. but if you need strict isolation docker is your man, focussing on security and portability without affecting the performance.

But let's say you are new to development and say "bro i am just starting out and i don't need to focus on security right now", yeah even though you are starting out new and you dont need to focus on security right now but you should be some essential security concepts for project integrity but leaving that aside docker can help you in the development process as well and it will be mind blowing.

I am not going to tell you some example from the internet or from the documnetation but, i am going to tell you my real-time example so that you will know the entire potential of the docker and who knows you might take interest in it and become contributors to enhance it as well. Anyways when i was bulding my `mini-project` named `life-calendar-widget` which is a fun project that built to keep myself to stay focussed and to be productive wihtout losing the sight of my goal. ooh feeling interested i will add the [link here](https://kenwolverine1.github.io/posts/life_calendar_widget_project_log1/) feel free to check it out;>

While i was building the project i was required to re-run the project frequently when ever i made changes to the source code which made me lose my focus more often and as a person who is thriving for productivity and efficiency i felt let down so i was searching a way to solve this problem so that i can focus on logic of the project than spending the time restarting the electron development server. when i was searching to solve this problem efficiently, i came across docker and i was suprised to know that docker can solve this problem. it's not like i was not aware of docker's existence but before knowing this i was having this picture in mind that it helps developers package their softwares as containers and used it to run on shared OS as production softwares but, after learning about it i came to know that docker can do `service isolation` meaning clean install and deletion without a hassle,`portability`- can be used in any system, `CI/CD integration`- used to integrate with CI/CD easily

After knowing that docker can solve my issue i was happy to look into it to learn more about it and i was so sure that it was worth learning and it was.

## Docker containers vs Images:-

I thought that containers and images are same by thinking that it just have different names to differentiate based on the type and environment for example images are the names when creating the file and containers are the names when executing the file but when i started learning docker i came to know that both are two different things each having their own differences. I thought of adding this to this blog because who knows there might be a lot of people thinking like me and i want this to be the one place where people can learn entirely about docker without searching multiple resources. i want this to be a goto resource or cheatsheet when it comes to docker so i am writing this blog keeping that in mind

## Images:-
1. A docker image is a `blueprint` or `template` to run an application inside a container and they are `immutable` (can't be changed once created)

2. A docker image includes application code, dependencies, config files, file system files and dockerfile(used to write instructions to execute app) or docker-compose file(used when there are multiple instructions for multiple apps)

3. A docker image is built using `docker build` command

## Containers:-
1. A docker container is a `running instance` of a `docker image` and they are `mutable` ( can be changed after creating it)

2. they are isolated from the system but run on same kernel

3. docker containers are built using `docker run` command

## Docker engine & Docker CLI:-

Docker engine is the open source tech used to containerize our applications and it acts as a cliet-server application with client `docker` and server with daemon `dockerd`. The docker client uses docker API to communicate with docker daemon

Docker client is a command line interface(CLI) named `docker`

## Installing Docker:-

In order to install docker in fedora 41 there are two ways,

1. you can setup docker's repository and install from them which is easy to use and update and it is the recommended approach as well

2. you can download the RPM(Redhat Package Manager) package and install it manually which makes the updates to be manually installed as well and better suited for situations where internet access is limited

I am going to go with recommended approach but feel free to use any kind of approach

### Setting up the repo:-

we need to install `dnf-plugins-core` to setup the repo
```sh
sudo dnf -y install dnf-plugins-core
```

then we need to add the official docker repo
```sh
sudo dnf-3 config-manager --add-repo \
 https://download.docker.com/linux/fedora/docker-ce.repo
```

now let's install docker
```sh
sudo dnf install docker-ce docker-ce-cli \
containerd.io docker-buildx-plugin \
docker-compose-plugin
```

## Configuring docker to solve permission denied when trying to connect to docker daemon socket:-

This problem arises when you try to access docker without `sudo` command. which means you need to access as a `root` user everytime you use docker and that is not considered good due to security reasons. In order to solve this problem you can create a docker group and add your user 

create your group
```sh
sudo groupadd docker
```

add your user
```sh
sudo usermod -aG docker ${USER}
```

>**Note**: you have to log out and log in so that the group can be revaluated or you can use below command. If you log out and logged in you don't need to use the below command

```sh
su -s ${USER}
```

verify whether you can run docker as a non-root user
```sh
docker run hello-world
```

>**Note**: If you ran docker CLI commands using sudo before adding user to docker group you might get an error saying that group docker was created with incorrect permission. to fix the problem run the below commands

```sh
sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
sudo chmod g+rwx "$HOME/.docker" -R
```

## Common docker CLI commands:-

### docker start:-
To start the docker engine
```sh
systemctl start docker
```
To start docker automatically when the system is booted
```sh
systemctl enable --now docker
```

### docker process:-
To view all the running process
```sh
docker ps
```

### docker stop:-
To stop the docker daemon
```sh
systemctl stop docker
systemctl stop docker.socket
```

### restart docker:-
To  restart docker
```sh
systemctl restart docker
```

### docker pull:-
To pull image from docker hub
```sh
docker pull "IMAGE"
```

### local images:-
To see all images that are available locally
```sh
docker images
```

### remove a container:-
To remove a docker container
```sh
docker rm "CONTAINER_NAME or ID"
```

### remove an image:-
To remove a docker image
```sh
docker rmi "IMAGE_NAME"
```

### access logs:-
To access logs of a particular container
```sh
docker logs "CONTAINER"
```

### kill a running container:-
To kill a running container
```sh
docker kill "CONTAINER"
```

## Dockerfile:-

Dockerfile is a text file used to write instructions to create a docker image. There are several commands available to create a docker file and i am going to share the most common commands which i use regularly

>**Note**: Each command in dockerfile adds a layer above the base image making it complex and taking up more space so, in order to reduce complexity keep it minimum as possible


| Instructions        | Description                                  |
| ------------------- | -------------------------------------------- |
| `FROM`              | Create a new build stage from a base image   |
| `RUN`               | Execute build commands                       |
| `COPY`              | Copy files and directories                   |
| `WORKDIR`           | Change work directory                        |
| `ENV`               | Set environmental variables                  |
| `EXPOSE`            | Describes the port for application to listen |
| `CMD`               | default xecution commands                    |
| `HEALTHCHECK`       | check containers health on startup           |


The commands are not case sensitive but using capitalized letters is used to distinguish commands from arguments and is considered best practice

Let me show you an example of a dockerfile

```dockerfile
FROM Node:18
WORKDIR /app
COPY package.json package-lock.json
RUN npm install
COPY . .
EXPOSE 5000
ENV NODE_ENV production
CMD ["npm" "start"]
```

1. The `FROM` is used to add a base image which acts as a base to your build

2. The `WORKDIR` is used to specify the working directory where the `COPY`,`RUN` and `CMD` commands take place

3. The `COPY` is used to copy the files from source to destination and `.` implies current directory

4. The `RUN` is used to execute commands in the container at build time

5. The `EXPOSE` is used to expose the port of the container/image

6. The `ENV` is used to set environment variables in images 

7. The `CMD` is used to set the default execution command of the container 

## Docker Image:-

### Docker build:-
A docker image is built using 
```sh
docker build [options] path | url | -
```
path = the path to your directory containing the dockerfile and `.` for current directory
`url` =  ususally a git repository containing a dockerfile \
`-` = used to pass the docker file as standard input which is very useful when scripting automation

now let's discuss the options, the most commonly used are,

>**Note**: replace the `" "` with your own values including the `"`

-t = used to tag the image with a `name of your choice and tags` but the tag is optional
```sh
docker build -t "NAME":"TAG" .
```

-f = used to specify the name of the dockerfile with `name of your choice`
```sh
docker build -f "DOCKERFILE NAME" -t "NAME":"TAG" .
```

--no-cache = used to disable the cache forces the dockerfile to rerun all steps in file without using cached layers. this is best when you want to use only the latest version of image
```sh
docker build --no-cache -t "NAME" .
```
--build-arg = used to pass buid time arguments
```sh
docker build --build-arg VERSION=1.0 -t "NAME" .
```

-m = used to set memory limit during the build
```sh
docker build -m 4g -t "NAME" .
```

these are the most commonly used options atleast that's what i use but if you need other commands i will attach the official documentation [link here](https://docs.docker.com/reference/cli/docker/buildx/build/)

### Docker Push:-

### docker login:-
To login to your docker hub
```sh
docker login
```
after that enter your credintials such as `username` and `password`

### push your container:-
```sh
docker push "CONTAINER_NAME"
```

### logout if needed:-
```sh
docker logout
```

### Docker ignore:-

dockerignore file is a text file which is used to exclude files and directories from copied into your docker image during build process and it works just like gitignore file

```sh
node_modules
.git
*.log
Dockerfile
.dockerignore
.env
```

### Base Images:-

Base images are considered as foundation of your container. it can be a `minimal OS`,a `language`,a `runtime` or `scratch` (used to build from nothing)

## Docker Container:-

### Docker Run:-
A docker container is built using
```sh
docker run [options] image [command] [ags..]
```

image = the name of the docker image that you wanted to use to create a container
command = the command you want to run inside the container which is optional
args = the arguments passed to the container which is optional as well

now let's discuss the options, the most commonly used options are,

-d = used to run the container in detached mode which runs the container in backgroud 
```sh
docker run -d "IMAGE"
```

-p = used to expose the container port to host machine. best used for micro-services
```sh
docker run -p 8080:8000 "IMAGE"
```

-e = used to set environment variables inside the container
```sh
docker run -e ENV=value "IMAGE"
```

--name = used to assign a name to the container. by default if no name is given a random name will be assigned
```sh
docker run --name "NAME" "IMAGE"
```

-v = used to mount volume from host machine
```sh
docker run -v "/home/path:/container/path "IMAGE"
```

-it = used to attach a terminal session to the container, -i keeps the container running and -t allocates a terminal session to it
```sh
docker run -it "IMAGE"
```

--rm = this removes the container when it exits. useful for one time tasks like testing etc..
```sh
docker run --rm "IMAGE"
```

--network = used to specify the network mode of the container. the below command connects container directly to host network
```sh
docker run --network host "IMAGE"
```

these are the most commonly used options, but if you need other commands i will attach the official documentation [link here](https://docs.docker.com/reference/cli/docker/container/run/)

### Docker Exec:-

>**Note**: This works only on the already running containers

This is used to execute commands inside the container in real-time
```sh
docker exec [options] "CONTAINER_NAME or ID" [command] [args..]
```
command = the command you want to run inside the container
args = the arguments passed to the container which is optional

now let's discuss the options, the most commonly used options are,

-d = used to run the container in detached mode which runs the container in backgroud 
```sh
docker exec -d "CONTAINER" touch /tmp/file
```

-it = used to execute a terminal session to the running container
```sh
docker exec -it "CONTAINER" sh
```

these are the most commonly used options, but if you need other commands i will attach the official documentation [link here](https://docs.docker.com/reference/cli/docker/container/exec/)

## Docker Compose:-

Docker compose is a `YAML` file which is used to run multiple containers at the same time which is ideal if you have multiple services to work together such as micro-services etc...

>**Note**: Since this is a very big topic and i haven't had my hands on it yet so let me post it in a seperate post in detail and don't worry guys i will definitely post it 


## Docker Networking:-

there are commands used to maintain networks for docker

### Connect to a network:-
to connect a container to a network
```sh
docker network connect "NETWORK_NAME" "CONTAINER_NAME"
```

### Create a network:-
To create a network
```sh
docker network create "NETWORK_NAME"
```

### Run containers on a custom network:-
To run multiple containers on a custom network
```sh
docker run -d --network "NETWORK_NAME" --name "CONTAINER_NAME_1"
docker run -d --network "NETWORK_NAME" --name "CONTAINER_NAME_2"
```

### Dissconnect a network:-
To discoonect a container from a network
```sh
docker network disconnect "NETWORK_NAME" "CONTAINER_NAME"
```

### List networks:-
To list all the networks
```sh
docker network ls
```

### Remove all unused networks:-
To remove all unused networks
```sh
docker network prune
```

### Remove one or more networks:-
To remove just one or more networks
```sh
docker network rm "NETWORK_NAME"
```

### Display info on network
To display detailed info on one or more networks
```sh
docker network inspect "NETWORK_NAME"
```

## Best Practices:-

Based on my experience i would suggest few things such as,

1. keep your commands in docker file as minimum as possible by combining commands because each command adds a layer to your base image

2. Instead of using big images such as `ubuntu`,`fedora` and `debian` try to use specific images based on your requirements such as `node`,`python`,`openjdk` and `alphine` which helps you to be efficient

3. Instead of using `latest` tag for image try using something specific

4. try to add name to your container using `--name` tag

5. use dockerignore file to exclude unwanted files

6. try to use `RUN` as minimum as possible

7. keep dockerfile instructions in right order


