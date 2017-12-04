# Docker-Machine
### Docker machine installation and configuration guide OS Ubuntu

#### Install Docker machine on Linux , For OS other than Linux please go to link https://docs.docker.com/machine/install-machine/

$ sudo curl -L https://github.com/docker/machine/releases/download/v0.13.0/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine <br />
$ sudo chmod +x /tmp/docker-machine <br />
$ sudo cp /tmp/docker-machine /usr/local/bin/docker-machine <br />

### Installation verification 

$ sudo docker-machine version
- Expected Output - docker-machine version 0.13.0, build 9371605

## Virtual box installation 

$ sudo apt-get install curl (Optional if curl package is not available) <br />
$ sudo cd /tmp/ && sudo curl -O http://download.virtualbox.org/virtualbox/5.1.22/virtualbox-5.1_5.1.22-115126~Ubuntu~xenial_amd64.deb  <br />
$ sudo dpkg -i virtualbox-5.1_5.1.22-115126~Ubuntu~xenial_amd64.deb <br />

### IF "Package Error" Re-run 
$ sudo apt-get -f install

##### Error with pre-create check: "This computer doesn't have VT-X/AMD-v enabled. Enabling it in the BIOS is mandatory
##### Enable VT from BIOS Re-run 

## Creating Swarm Cluster using Docker Machine

