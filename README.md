# iBrew docker container #

## Using ##
Build yourself a local copy of this container:

```
$ git clone https://github.com/biwhite/docker-ibrew.git

$ cd docker-ibrew

$ docker build -t biwhite/ibrew .
```

Run with:

```
docker run --name ibrew -d -p 2080:2080 -v /opt/ibrew:/root/.iBrew -v /var/run/dbus/system_bus_socket:/var/run/dbus/system_bus_socket biwhite/alpine-ibrew
```

Obtain a shell within the running environment with:

```
docker exec -it ibrew /bin/bash
```

View logs the app is producing:

```
docker logs -f ibrew
```

Stopping/Starting/Removing container

```
docker stop ibrew
docker start ibrew
docker rm ibrew
```

If using the volume mappings above
  * License file will be in /opt/ibrew/.ibrew
  * Logs will be in /opt/ibrew/logs/
  * Machines should each have their own file, /opt/ibrew/x.x.x.x.conf

You can view the iBrew app announcing itself using the ```avahi-browse -a``` command on the host, or other machines on your network.

## TODO ##

  * Communicating outside of docker not yet working

## Links ##

  * iBrew - https://github.com/Tristan79/iBrew
  * Alpine linux - https://alpinelinux.org/
  * s6 overlay - https://github.com/just-containers/s6-overlay
