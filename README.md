# Docker-Machine
### Docker machine installation and configuration guide OS Ubuntu

#### Install Docker machine on Linux
For OS other than Linux please go to link [Docker Machine] (https://docs.docker.com/machine/install-machine/).

```
$ sudo apt-get update -y 
$ sudo curl -L https://github.com/docker/machine/releases/download/v0.13.0/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine 
$ sudo chmod +x /tmp/docker-machine 
$ sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
```
### Installation verification 

```
$ sudo docker-machine version
```
- Expected Output - docker-machine version 0.13.0, build 9371605

## Virtual box installation 
```
$ sudo apt-get install curl (Optional if curl package is not available)
$ sudo cd /tmp/ && sudo curl -O http://download.virtualbox.org/virtualbox/5.1.22/virtualbox-5.1_5.1.22-115126~Ubuntu~xenial_amd64.deb
$ sudo dpkg -i virtualbox-5.1_5.1.22-115126~Ubuntu~xenial_amd64.deb
```
### IF "Package Error" Re-run 
```
$ sudo apt-get -f install
```
##### Error with pre-create check: "This computer doesn't have VT-X/AMD-v enabled. Enabling it in the BIOS is mandatory
##### Enable VT from BIOS Re-run 

## Creating Swarm Cluster using Docker Machine
```
$ sudo docker-machine create -d virtualbox --virtualbox-cpu-count="1" --virtualbox-disk-size="4000" --virtualbox-memory="1024" swarmmanager
$ sudo docker-machine create -d virtualbox --virtualbox-cpu-count="1" --virtualbox-disk-size="4000" --virtualbox-memory="1024" swarmnode1
$ sudo docker-machine create -d virtualbox --virtualbox-cpu-count="1" --virtualbox-disk-size="4000" --virtualbox-memory="1024" swarmnode2
```
## Verify Swarm Cluster
```
$ sudo docker-machine ls 
```
## Exploring enviornment of nodes 
```
$ sudo docker-machine env swarmmanager
```
## Switching to Swarmmanager Machine, or any node $ docker-machine ssh "nodename" 
```
$ docker-machine ssh swarmmanager
OR
$ eval $(docker-machine env swarmmanager)
```
## Initate a container for funtionality check 
```
$ docker run hello-world
```
## Switching back to main Docker host, Below command unset enviornment of swarmanager to switch you back to Docker host
```
$ exit
OR
$ eval $(docker-machine env -u)
```
### Docker Machine Help

  **active**                Print which machine is active 
  config                Print the connection config for machine 
  create                Create a machine
  env                   Display the commands to set up the environment for the Docker client
  inspect               Inspect information about a machine
  ip                    Get the IP address of a machine
  kill                  Kill a machine
  ls                    List machines
  regenerate-certs      Regenerate TLS Certificates for a machine
  restart               Restart a machine
  rm                    Remove a machine
  ssh                   Log into or run a command on a machine with SSH.
  scp                   Copy files between machines
  start                 Start a machine
  status                Get the status of a machine
  stop                  Stop a machine
  upgrade               Upgrade a machine to the latest version of Docker
  url                   Get the URL of a machine
  
  
  ## Docker Machine on Cloud / AWS 



