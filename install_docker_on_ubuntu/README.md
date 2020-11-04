# Straight-forward Docker engine install on Ubuntu and CentOS

# 1. Install on Centos

## Prerequisites

Uninstall older version of docker

```
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

It’s OK if yum reports that none of these packages are installed.


## SET UP THE REPOSITORY

Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```
sudo yum install -y yum-utils

sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

## Install Docker 

	sudo yum install docker-ce docker-ce-cli containerd.io

Start Docker

	sudo systemctl start docker

Verity that Docker Engine is installed correctly

	sudo docker run hello-world


## If you want to unninstall Docker, use the following commands

```
sudo yum remove docker-ce docker-ce-cli containerd.io
sudo rm -rf /var/lib/docker
```

# 2. Install on Ubuntu

## Prerequisites

To get started with Docker Engine on Ubuntu, make sure you have one of following OS

- Ubuntu Focal 20.04 (LTS)
- Ubuntu Bionic 18.04 (LTS)
- Ubuntu Xenial 16.04 (LTS)

Uninstall older version of docker

        sudo apt-get remove docker docker-engine docker.io containerd runc


It’s OK if apt-get reports that none of these packages are installed.


## SET UP THE REPOSITORY

1. Update the apt package index and install packages to allow apt to use a repository over HTTPS:

```
sudo apt-get update

sudo apt-get install \
apt-transport-https \
ca-certificates \
curl \
gnupg-agent \
software-properties-common
```

2. Add Docker’s official GPG key:

        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

3. Setup the stable repository

```
sudo add-apt-repository \
"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) \
stable"
```

## Install Docker 

```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Verity that Docker Engine is installed correctly

        sudo docker run hello-world


## If you want to unninstall Docker, use the following commands

```
sudo apt-get purge docker-ce docker-ce-cli containerd.io
sudo rm -rf /var/lib/docker

