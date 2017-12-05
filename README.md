# Docker-Machine
### Docker machine installation and configuration guide OS Ubuntu

#### Install Docker machine on Linux , For OS other than Linux please go to link https://docs.docker.com/machine/install-machine/

```
$ sudo apt-get update -y` <br />
$ sudo curl -L https://github.com/docker/machine/releases/download/v0.13.0/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine <br />
$ sudo chmod +x /tmp/docker-machine <br />
$ sudo cp /tmp/docker-machine /usr/local/bin/docker-machine <br />
```
### Installation verification 

```
$ sudo docker-machine version
```
- Expected Output - docker-machine version 0.13.0, build 9371605

## Virtual box installation 
```
$ sudo apt-get install curl (Optional if curl package is not available) <br />
$ sudo cd /tmp/ && sudo curl -O http://download.virtualbox.org/virtualbox/5.1.22/virtualbox-5.1_5.1.22-115126~Ubuntu~xenial_amd64.deb  <br />
$ sudo dpkg -i virtualbox-5.1_5.1.22-115126~Ubuntu~xenial_amd64.deb <br />
```
### IF "Package Error" Re-run 
```
$ sudo apt-get -f install
```
##### Error with pre-create check: "This computer doesn't have VT-X/AMD-v enabled. Enabling it in the BIOS is mandatory
##### Enable VT from BIOS Re-run 

## Creating Swarm Cluster using Docker Machine
```
$ sudo docker-machine create -d virtualbox --virtualbox-cpu-count="1" --virtualbox-disk-size="4000" --virtualbox-memory="1024" swarmmanager <br />
$ sudo docker-machine create -d virtualbox --virtualbox-cpu-count="1" --virtualbox-disk-size="4000" --virtualbox-memory="1024" swarmnode1 <br />
$ sudo docker-machine create -d virtualbox --virtualbox-cpu-count="1" --virtualbox-disk-size="4000" --virtualbox-memory="1024" swarmnode2 <br />
```
## Verify Swarm Cluster
```
$ sudo docker-machine ls 
```
## Exploring enviornment of nodes 
```
$ sudo docker-machine env swarmmanager <br />
```
## Switching to Swarmmanager Machine, or any node $ docker-machine ssh "nodename" 
```
$ docker-machine ssh swarmmanager <br />
OR <br />
$ eval $(docker-machine env swarmmanager)
```
## Initate a container for funtionality check 
```
$ docker run hello-world <br />
```
## Switching back to main Docker host, Below command unset enviornment of swarmanager to switch you back to Docker host
```
$ exit <br />
OR <br />
$ eval $(docker-machine env -u)
```
### Docker Machine Help

$ docker-machine --help <br />
Usage: docker-machine [OPTIONS] COMMAND [arg...] <br />

Create and manage machines running Docker.<br />

Version: 0.4.0 (9d0dc7a)<br />

Author:<br />
  Docker Machine Contributors - <https://github.com/docker/machine><br />

Options:<br />
  --debug, -D                                   Enable debug mode<br />
  -s, --storage-path "/root/.docker/machine"    Configures storage path [$MACHINE_STORAGE_PATH]<br />
  --tls-ca-cert                                 CA to verify remotes against [$MACHINE_TLS_CA_CERT]<br />
  --tls-ca-key                                  Private key to generate certificates [$MACHINE_TLS_CA_KEY]<br />
  --tls-client-cert                             Client cert to use for TLS [$MACHINE_TLS_CLIENT_CERT]<br />
  --tls-client-key                              Private key used in client TLS auth [$MACHINE_TLS_CLIENT_KEY]<br />
  --native-ssh                                  Use the native (Go-based) SSH implementation. [$MACHINE_NATIVE_SSH]<br />
  --help, -h                                    show help<br />
  --version, -v                                 print the version<br />

Commands:<br />
  active                Print which machine is active<br />
  config                Print the connection config for machine<br />
  create                Create a machine<br />
  env                   Display the commands to set up the environment for the Docker client<br />
  inspect               Inspect information about a machine<br />
  ip                    Get the IP address of a machine<br />
  kill                  Kill a machine<br />
  ls                    List machines<br />
  regenerate-certs      Regenerate TLS Certificates for a machine<br />
  restart               Restart a machine<br />
  rm                    Remove a machine<br />
  ssh                   Log into or run a command on a machine with SSH.<br />
  scp                   Copy files between machines<br />
  start                 Start a machine<br />
  status                Get the status of a machine<br />
  stop                  Stop a machine<br />
  upgrade               Upgrade a machine to the latest version of Docker<br />
  url                   Get the URL of a machine<br />
  help, h               Shows a list of commands or help for one command<br />
  
  ## Docker Machine on Cloud / AWS 



