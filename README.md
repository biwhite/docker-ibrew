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
docker run --name ibrew -d -v /opt/ibrew:/etc/iBrew \
  -v /var/run/dbus/system_bus_socket:/var/run/dbus/system_bus_socket \
  -p 2080:2080 biwhite/ibrew
```

If you want auto-discovery to work, then you need to include ```--net=host``` as it uses IP broadcast messages to find devices.

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
  * You will now have an iBrew web UI running on http://localhost:2080/

You can view the iBrew app announcing itself using the ```avahi-browse -a``` command on the host, or other machines on your network.

## Links ##

  * iBrew - https://github.com/Tristan79/iBrew
  * Alpine linux - https://alpinelinux.org/
  * s6 overlay - https://github.com/just-containers/s6-overlay
