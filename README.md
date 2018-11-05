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
List running containers: `docker ps`

#### Images
Build image:
- `cd` to the directory with Dockerfile
- `docker build -t DOCKER_NAME .`
List images: `docker image ls`
Delete image: `docker image rm [-f] IMAGE`

## Data Science
Start with [Jupyter Docker Stack](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook)'s [Scipy Notebook](https://hub.docker.com/r/jupyter/scipy-notebook/)

Install:
`docker pull jupyter/scipy-notebook`
Run:
`docker run --rm -p 8888:8888 -v ~/projects:/home/jovyan/work/ jupyter/scipy-notebook`


## Deep Learning
There are many deep learning ready docker image available on GitHub. The following two are tested and ready to run.

### CPU only with Jupyter
Setup:
https://hub.docker.com/r/waleedka/modern-deep-learning/
Run:
`docker run -it -p 8888:8888 -p 6006:6006 -v ~/:/host waleedka/modern-deep-learning jupyter notebook --ip=0.0.0.0 --allow-root /host`

### GPU with Jupyter
Setup:
https://github.com/ufoym/deepo#Jupyter
Run:
`nvidia-docker run -it -p 8888:8888 -v ~/:/host --ipc=host ufoym/deepo:all-py36-jupyter jupyter notebook --no-browser --ip=0.0.0.0 --allow-root /host --NotebookApp.token= --notebook-dir='/root'`

### Build my own
Setup:
`docker build -t tf-object-detection .`
Run:
`docker run -it -p 8888:8888 -p 6006:6006 -v ~/:/host tf-object-detection jupyter notebook --ip=0.0.0.0 --allow-root /host`


## Investment
