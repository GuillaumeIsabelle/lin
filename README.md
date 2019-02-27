# lin
Lin is Containerizing Linux Fedora Platform where I intend to migrate my good old LAMP in Docker container.


___

```bash

# Install key

## Generate 
ssh-keygen

# install git
dnf install -y git


```

____


# Install docker
```bash

## Remove old stuff
sudo dnf remove -y docker                   docker-client                   docker-client-latest                   docker-common                   docker-latest                   docker-latest-logrotate                   docker-logrotate                   docker-selinux                   docker-engine-selinux                   docker-engine

## Install prereq
dnf -y install dnf-plugins-core
 dnf config-manager     --add-repo     https://download.docker.com/linux/fedora/docker-ce.repo
 
## Install docker
dnf install -y docker-ce docker-ce-cli containerd.io


#Docker Compose
 dnf install -y docker-compose
 
```

## Start and enable docker

```bash
systemctl start docker
 systemctl enable docker
```


# Post install
```bash
su -
docker login

# test
 docker run hello-world

```
