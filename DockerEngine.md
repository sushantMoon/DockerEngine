# Docker Engine Installation

## Steps 

1. Remove Docker (this won't delete images, containers, volumes, or customized configuration files):
	```sh
	sudo apt-get purge docker-engine
	```
2. Remove the Docker apt key:
	```sh
	sudo apt-key del 58118E89F3A912897C070ADBF76221572C52609D
	```
3. Delete the docker.list file:
	```sh
	sudo rm /etc/apt/sources.list.d/docker.list
	```
4. Manually delete apt cache files:
	```sh
	sudo rm /var/lib/apt/lists/apt.dockerproject.org_repo_dists_ubuntu-xenial_*
	```
5. Run apt-get update:
	```sh
	sudo apt-get update
	```
6. Install apt-transport-https and ca-certificates again:
	```sh
	sudo apt-get install apt-transport-https ca-certificates  curl software-properties-common
	```
7. Add the apt key:
	```sh
	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
	```
8. Add the docker.list file :
	```sh
	echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" | sudo tee /etc/apt/sources.list.d/docker.list
	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
	```
9. Run apt-get update:
	```sh
	sudo apt-get update
	```
10. Install Docker:
	```sh
	sudo apt-get install docker-engine
	```


## Testing Installation

Run : `docker run hello-world`

This should return a message very similar to the following :

```sh
	Hello from Docker!
	This message shows that your installation appears to be working correctly.

	To generate this message, Docker took the following steps:
	 1. The Docker client contacted the Docker daemon.
	 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
	 3. The Docker daemon created a new container from that image which runs the
	    executable that produces the output you are currently reading.
	 4. The Docker daemon streamed that output to the Docker client, which sent it
	    to your terminal.

	To try something more ambitious, you can run an Ubuntu container with:
	 $ docker run -it ubuntu bash

	Share images, automate workflows, and more with a free Docker ID:
	 https://cloud.docker.com/

	For more examples and ideas, visit:
	 https://docs.docker.com/engine/userguide/
```

Some More testing , running ubuntu bash :

```sh
	sudo docker run -it ubuntu bash
```
This shall start an isolated environment with Ubuntu's Bash
To exit, enter `exit`.


To delete these images and the containers, first delete the containers using container names and then the image using image names, they can be found using,

```sh
	sudo docker ps -as
```

Deleting the container :

```sh
	sudo docker rm frosty_bell
	sudo docker rm confident_haibt
```

Deleting the images :

```
	sudo docker image rm ubuntu
	sudo docker rmi hello-world
```
Note : for deleting the images, both the commands seem to be equivalent. 


# Reference 

* https://docs.docker.com/engine/installation/linux/ubuntu/#install-using-the-repository
* https://stackoverflow.com/questions/41133455/docker-repository-does-not-have-a-release-file-on-running-apt-get-update-on-ubun
* https://stackoverflow.com/questions/33907835/docker-error-cannot-delete-docker-container-conflict-unable-to-remove-reposito
