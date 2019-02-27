# lin
Lin is Containerizing Linux Fedora Platform where I intend to migrate my good old LAMP in Docker container.


___

# Install key and Git
```bash


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


___
# --@v File Accessibility
## Samba
```bash
dnf -y install samba samba-client

## see /etc/samba/smb.conf sample on : 
### --@urir https://github.com/GuillaumeIsabelle/lin/blob/master/etc/samba/smb.conf

#Checkout the repo
mkdir /etc/lin && cd /etc/lin/ &&   git clone git@github.com:GuillaumeIsabelle/lin.git .
cat /etc/lin/etc/samba/smb.conf etc/samba

## Share dir
mkdir -m 777 /home/share

#Enable service
systemctl start smb nmb
systemctl enable smb nmb

#Firewall
firewall-cmd --add-service=samba --permanent
firewall-cmd --reload
setsebool -P samba_enable_home_dirs on
# SE
restorecon -R /home/share
reboot

```