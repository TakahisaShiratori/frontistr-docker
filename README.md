# frontistr-docker
Run [FrontISTR](https://github.com/FrontISTR/FrontISTR) on Docker
## Usage
Pull from [Docker Hub](https://hub.docker.com/r/takashiratori/frontistr), or built Docker image locally
### Pull from Docker Hub
Prepare input files for FrontISTR, and run the container
```
$ ls
hecmw_ctrl.dat	hinge.cnt	hinge.msh
$ docker run -v $(pwd):/home/frontistr takashiratori/frontistr:V46
```
### Built Docker image locally
Clone this repository, and build the image
```
$ git clone git@github.com:TakahisaShiratori/frontistr-docker.git
$ cd frontistr-docker/V46/
$ docker build -t frontistr:V46 .
```
