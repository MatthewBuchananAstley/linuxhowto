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

# Docker images 

Overzicht van gecreëerde images:

    [matthew@localhost app]$ docker image ls
    REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
    getting-started     latest              109080232897        8 minutes ago       404 MB
    docker.io/node      12-alpine           bb6d28039b8c        7 months ago        91 MB

Overzicht van actieve docker images:

    [matthew@localhost app]$ docker ps
    CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
    1adb2655be40        getting-started     "docker-entrypoint..."   About an hour ago   Up About an hour    0.0.0.0:3000->3000/tcp   silly_keller

Stoppen van actieve images:

    [matthew@localhost app]$ docker stop 1adb2655be40
    1adb2655be40

Docker images verwijderen:

    [matthew@localhost app]$ docker image rm getting-started
    Untagged: getting-started:latest
    Deleted: sha256:109080232897c3f4ab17760f961d58bcc02841624b38e2cb22ee69d4e49c6b8b
    Deleted: sha256:7b8882ab98b03d8a7ea80d317eaa0dafa4c9e86878fcc0fff66c90ebee0c8d82
    Deleted: sha256:6f7298b5eb53e2897fa1d9f312a5537b3fbbd834b6cc7dd7ba861cd69a224a26
    Deleted: sha256:086a11b4110654946f0ed6982db42c58c4e5a05ad400496414f6fae2af410fa2
    Deleted: sha256:74a0e5053ac61d185698a1a510d9fba11f1c2b2fc7d20180770d73e2ba2873cf
    Deleted: sha256:b7d33a64b180af59916c5116c60e7fea31309e9dbfc582d5a343027e9c8463a4
    Deleted: sha256:a7be6ec3fd925cbd9c1d5463d79b1cf957b7a00684524231f3385f766ac3767c
    Deleted: sha256:bbca728b7be206f0dd04880e8a6d1a477d432b5cd9ba5bcffa998a89e3aa0f10
    Deleted: sha256:df88f60a41218c189d14c76eec8d39383a233ef8f8314eddc1af108deb8b322d
    Deleted: sha256:fe568c5973e730c689dc98f05c886d00d2eb759fba1194e6b405f02ca815c7f2

