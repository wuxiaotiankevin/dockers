# Docker
This repo holds a collection of useful dockers.

## Docker Basics
### Install Docker
See https://docs.docker.com/.

### Basics
An __image__ is an executable package with everything to run the service.

An __container__ is a runtime instance of an image.

### Useful Commands
#### Containers
List running containers:

`docker ps`

#### Images
Build image:
- `cd` to the directory with Dockerfile
- `docker build -t DOCKER_NAME .`

List images:

`docker image ls`

Delete image:

`docker image rm [-f] IMAGE`

Delete untagged images:

`docker rmi --force $(docker images --filter "dangling=true" -q --no-trunc)`


## Data Science
Start with [Jupyter Docker Stack](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook)'s [Scipy Notebook](https://hub.docker.com/r/jupyter/scipy-notebook/)

Install:

`docker pull jupyter/scipy-notebook`

Run:

`docker run --rm -p 8888:8888 -v ~/projects:/home/jovyan/work/ jupyter/scipy-notebook`


## Deep Learning
There are many deep learning ready docker image available on GitHub. The following two are tested and ready to run.

### Modern Deep Learning
Setup:

https://hub.docker.com/r/waleedka/modern-deep-learning/

or use my copy of Dockerfile

Run with command line:
`docker run -it -p 8888:8888 -p 6006:6006 -v ~/:/host modern-deep-learning`

Run with Jupyter:

`docker run -it -p 8888:8888 -p 6006:6006 -v ~/projects:/host modern-deep-learning jupyter notebook --ip=0.0.0.0 --allow-root /host`

### Deepo

#### CPU

Setup:

https://github.com/ufoym/deepo#CPU

Run:

`docker run -it -p 8888:8888 -v $PWD:/root --ipc=host ufoym/deepo:all-py36-jupyter-cpu jupyter notebook --no-browser --ip=0.0.0.0 --allow-root --NotebookApp.token= --notebook-dir='/root/'`


#### GPU
Setup:

https://github.com/ufoym/deepo#Jupyter

Run:

`docker run --runtime=nvidia -it -p 8888:8888 -v $PWD:/root --ipc=host ufoym/deepo:all-jupyter-py36 jupyter notebook --no-browser --ip=0.0.0.0 --allow-root --NotebookApp.token= --notebook-dir='/root/'`


### Build my own

#### tf-object-detection

Setup:

`docker build -t tf-object-detection .`

Run:

`docker run -it -p 8888:8888 -p 6006:6006 -v ~/:/host tf-object-detection jupyter notebook --ip=0.0.0.0 --allow-root /host`

#### tensorflow-gpu-jupyter

Setup:

`cd ./tf-gpu-jupyter`
`docker build -t dl-gpu-jupyter .`

Run:

`docker run --runtime=nvidia -it -p 8888:8888 -v $PWD:/root --ipc=host dl-gpu-jupyter jupyter notebook --no-browser --ip=0.0.0.0 --allow-root --NotebookApp.token= --notebook-dir='/root/'`

#### tensorflow-gpu

Setup:

`cd ./tf-gpu`
`docker build -t dl-gpu .`

Run:

`docker run --runtime=nvidia -it -v $PWD:/tmp -w /tmp dl-gpu bash`

#### tensorflow-cpu

Setup:

`cd ./tf-cpu`
`docker build -t dl-cpu-jupyter .`

Run:

`docker run --runtime=nvidia -it -p 8888:8888 -v $PWD:/root --ipc=host dl-cpu-jupyter jupyter notebook --no-browser --ip=0.0.0.0 --allow-root --NotebookApp.token= --notebook-dir='/root/'`


## Investment
Build image:
- `cd` to ./investment/
- `docker build -t invest .`

Run:

`docker run --rm -p 8888:8888 -v ~/projects:/home/jovyan/work/ invest`
