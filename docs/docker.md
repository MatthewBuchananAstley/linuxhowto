# Docker containers

# Getting started tutorial

https://docs.docker.com/get-started/02_our_app/

# Docker installeren op CentOS 7

    yum install docker-latest

# docker.sock permission denied error verhelpen op centos

Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post http://%2Fvar%2Frun%2Fdocker.sock/v1.26/build?buildargs=%7B%7D&buildbinds=null&cachefrom=%5B%5D&cgroupparent=&cpuperiod=0&cpuquota=0&cpusetcpus=&cpusetmems=&cpushares=0&dockerfile=dockerfile&labels=%7B%7D&memory=0&memswap=0&networkmode=default&rm=1&shmsize=0&t=getting-started&ulimits=null: dial unix /var/run/docker.sock: connect: permission denied

Docker moet gestart worden met een default docker groep daarom "-G dockerroot-latest" toevoegen aan:

    /etc/sysconfig/docker-latest
    OPTIONS='--selinux-enabled -G dockerroot-latest'

De user toevoegen aan de dockerroot-latest groep:

    usermod -aG dockerroot-latest "username"

De user moet daarna opnieuw inloggen om de nieuwe groep te kunnen gebruiken.
