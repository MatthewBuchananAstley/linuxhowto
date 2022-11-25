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

# Docker images pushen naar docker hub registry

Met een gratis account bij docker hub (docker.io) kun je één registry creëeren, waarna er in te loggen is:

    docker login -u "gebruikersnaam" (het is hoofdlettergevoelig)

Een image op de lokale machine moet eerst een tag hebben voordat het gepusht kan worden:

    docker tag getting-started GEBRUIKERSNAAM/getting-started

Het pushen:

    docker push GEBRUIKERSNAAM/getting-started

Nadat een image gepushed is naar de docker hub registry kan het image gestart worden op een ander docker systeem (zoals lab.play-with-docker.com om te testen).
Zo'n image gestart op een ander systeem wordt "instance" genoemd.

# Aanhoudende data opslag

Containers zijn te starten op de volgende manier:

    docker run -d ubuntu bash -c "shuff -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"

Dat tail commando houdt de instance actief. Docker exec kan gebruikt worden. Voor het uitvoeren van commando's op een container:

    docker exec "container-id" cat /data.txt 

Opstarten van een nieuwe container met hetzelfde image:

    docker run -it ubuntu ls

Een storage volume maken:

    docker volume create todo-db

Voor het koppelen van het volume aan de container:

    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started

# Named volumes and bind mounts

<a href="https://docs.docker.com/get-started/06_bind_mounts/">https://docs.docker.com/get-started/06_bind_mounts/</a>

De twee voornaamste soorten volumes understeund door een standaard docker installatie zijn named volumes en bind mounts. Voor het gebruiken van andere soorten volumes zijn er zogenaamde "volume driver plugins". 

Docker volumes bekijken:

    docker volume ls
    docker volume inspect todo-db 

# Dev container starten voor een dev workflow

Het volgende docker commando zou een 12-alpine image moeten starten en yarn installeren en uitvoeren: 

    $docker run -dp 3000:3000 \
        -w /app -v "$(pwd):/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    000b2fcc81e338467a8b6f528378543240f351d9e8f1de423dc84041a7476a2b

Wanneer er een four optreedt dan wordt de container weer afgetuigd na het optuigen en print code, de container id. Met die code is het probleem met de container in het systeemlog te vinden.
Grep met tien regels erna en tien regels ervoor:

    #journalctl -xe | grep -A10 -B10 000b2fcc81e338467a8b6f528378543240f351d9e8f1de423dc84041a7476a2b

    Nov 24 11:30:16 localhost.localdomain oci-umount[7004]: umounthook <debug>: prestart container_id:000b2fcc81e3 rootfs:/var/lib/docker-latest/overlay2/b007653a87b21349733d56fbd14ad8f84f42d159365fccbf0152ad1d1f1f7036/merged
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]: yarn install v1.22.18
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]: Error: EACCES: permission denied, open '/app/package.json'
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]:     at Object.openSync (fs.js:462:3)
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]:     at Object.readFileSync (fs.js:364:35)
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]:     at onUnexpectedError (/opt/yarn-v1.22.18/lib/cli.js:88608:106)
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]:     at /opt/yarn-v1.22.18/lib/cli.js:88727:9
    Nov 24 11:30:16 localhost.localdomain oci-systemd-hook[7047]: systemdhook <debug>: 000b2fcc81e3: Skipping as container command is docker-entrypoint.sh, not init or systemd
    Nov 24 11:30:16 localhost.localdomain oci-umount[7048]: umounthook <debug>: 000b2fcc81e3: only runs in prestart stage, ignoring
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]: time="2022-11-24T11:30:16.425804559-05:00" level=error msg="containerd: deleting container" error="exit status 1: \"container 000b2fcc81e338467a8b6f528378543240f351d9e8f1de423dc84041a7476a2b does not exist\\none or more of the container deletions failed\\n\""
    Nov 24 11:30:16 localhost.localdomain kernel: docker0: port 1(veth664b57a) entered disabled state
    Nov 24 11:30:16 localhost.localdomain NetworkManager[968]: <info>  [1669307416.4736] manager: (vethe5c1915): new Veth device (/org/freedesktop/NetworkManager/Devices/111)
    Nov 24 11:30:16 localhost.localdomain kernel: docker0: port 1(veth664b57a) entered disabled state
    Nov 24 11:30:16 localhost.localdomain kernel: device veth664b57a left promiscuous mode
    Nov 24 11:30:16 localhost.localdomain kernel: docker0: port 1(veth664b57a) entered disabled state
    Nov 24 11:30:16 localhost.localdomain NetworkManager[968]: <info>  [1669307416.4890] device (veth664b57a): released from master device docker0
    Nov 24 11:30:16 localhost.localdomain dockerd-latest[1960]: time="2022-11-24T11:30:16.520972403-05:00" level=warning msg="000b2fcc81e338467a8b6f528378543240f351d9e8f1de423dc84041a7476a2b cleanup: failed to unmount secrets: invalid argument"

Een rechten probleem.

Het log continu bekijken kan met:

    journalctl -f

Na wat andere commando's uit te voeren om te zien wat dat rechtenprobleem is (ls ../ ; ls ../app)  blijkt dat er op CentOS een SElinux optie :z of :Z meegegeven moet worden met het bindmount commando:
    
    docker run -dp 3000:3000 -w /app -v "$(pwd):/app:z" node:12-alpine sh -c "yarn install && yarn run dev" 

Dat staat in de docker-run manpage:

    man docker-run | cat -n | grep -A5 -B5 ":z"
    644	
    645	       Labeling systems like SELinux require that proper labels are placed on volume content mounted into a container. Without a label, the  security  system  might
    646	       prevent the processes running inside the container from using the content. By default, Docker does not change the labels set by the OS.
    647	
    648	
    649	       To  change  a  label  in  the  container context, you can add either of two suffixes :z or :Z to the volume mount. These suffixes tell Docker to relabel file
    650	       objects on the shared volumes. The z option tells Docker that two containers share the volume content. As a result, Docker labels the content with  a  shared
    651	       content  label.  Shared  volume  labels  allow  all containers to read/write content.  The Z option tells Docker to label the content with a private unshared
    652	       label.  Only the current container can use a private volume.




