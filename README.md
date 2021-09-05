# JupyterLab Local Docker Image
This repository contains scripts to set-up a JupyterLab Docker Image with a Volume. The ```docker-compose.yml``` defines the JupyterLab image which will be pulled from Dockerhub. As an example, the pyspark-notebook is used as a base image, located here on [dockerhub](https://hub.docker.com/r/jupyter/pyspark-notebook/tags?page=1&ordering=last_updated). The full docs related to these docker images are located [here](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html)

## docker-compose explained
The ```docker-compose.yml``` file contains all the necessary configuration to get everything up and running. 

The docker image can be created and run using the following command:

```docker compose up```

### Image
A single service is created named 'app'. It is built from the pyspark notebooks on dockerhub. A specific version, or tag, can be pulled from dockerhub. In this example, tag 3.0.16 used. 

### Ports
The ports part details how we will access JupyterLabs from our web browser. In this example, we have mapped port 8888 on our local host to port 8888 in the docker container. As a result, we will be able to access JupyterLabs at ```http://127.0.0.1:8888/lab``` when we run the docker image. 

### Volumes
The volumes part defines how files will be shared between the host and the docker container. In this example we are sharing files that are located in the folder ```docker_local``` on our local machine, with the work folder in the docker image, located at ```/home/jovyan/worl```. **Note:** While the container maintains intact if the app service is exited, the volume ensures that no work will be lost in the event of the container being permantely deleted or other such unexpected events. 

### Environment
The last part specifies the necessary environmental variables to be enabled. To enable JupyterLabs, set ```JUPYTER_ENABLE_LAB=yes```

The official documentation for docker-compose can be found [here](https://docs.docker.com/compose/gettingstarted/)