# Machine Learning Docker Images

[![Docker Stars](https://img.shields.io/docker/stars/reufko/machinelearning.svg)][hub]
[![Docker Pulls](https://img.shields.io/docker/pulls/reufko/machinelearning.svg)][hub]

[hub]: https://hub.docker.com/r/reufko/machinelearning

This is a repository for various docker images created by [Reuf Kozlica](https://github.com/reufko) and [Max Schirl]() for the lecture on Machine Learning.

## Supported tags
* Ubuntu 18.04 based images:
  * **`anaconda-ubuntu` ([anaconda/ubuntu/Dockerfile](https://github.com/reufko/docker-images/blob/master/anaconda/ubuntu/Dockerfile))**
  * **`miniconda-ubuntu` ([miniconda/ubuntu/Dockerfile](https://github.com/reufko/docker-images/blob/master/miniconda/ubuntu/Dockerfile))**
  
* Alpine Linux 3.9 based images:
  * **`anaconda-alpine` ([anaconda/alpine/Dockerfile](https://github.com/reufko/docker-images/blob/master/anaconda/alpine/Dockerfile))**
  * **`miniconda-alpine` ([miniconda/alpine/Dockerfile](https://github.com/reufko/docker-images/blob/master/miniconda/alpine/Dockerfile))**
  
## Why?
The default docker images with python and anaconda usually have plenty of tools we don't need for the machine learning lecture. 
The other reason for creating this images is to enable all students to have the same version of different machine learning tools, 
in order to prevent version conflicts.

## Usage
First you will have to install [Docker](https://hub.docker.com/) for desktop on your computer. 
All of the images run a linux virtual machine on your computer and run a [Jupyter Notebook](https://jupyter.org/) in the background. 

Run command for Ubuntu 18.04 with Anaconda:

```shell
docker run --rm -ti -p 8888:8888 -v notebooks:/notebooks reufko/machinelearning:anaconda-ubuntu 
```
The command above will run the image which has a built in command to run Jupyter Notebook in the background on the port 8888. 
With the flag `-p 8888:8888` we are telling docker to map the port 8888 from the virtual machine to the port 8888 on the host machine.

**Important**: The flag `-v notebooks:/notebooks` tells docker that it should create a virtual volume on the host machine named notebooks and map 
it to the /notebooks folder in the virtual machine. If you don't specify this parameter your changes in the /notebooks folder 
(which is the default Jupyter Notebook folder) will not be persistant. E.g. your changes will be gone after shutting down the virtual machine.

As soon as the machine has been started you will be able to view the Jupyter Notebook by opening `http://localhost:8888` in your browser, 
or `http://<DOCKER-MACHINE-IP>:8888` if you are using a Docker Machine VM.
