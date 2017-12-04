# dockermachine
### Docker machine installation and configuration guide 
### Install Docker machine on Linux , For OS other than Linux please go to link https://docs.docker.com/machine/install-machine/
$ curl -L https://github.com/docker/machine/releases/download/v0.13.0/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine
$ chmod +x /tmp/docker-machine 
$ sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
### Installation verification 
$ docker-machine version
Expected Output - docker-machine version 0.13.0, build 9371605
