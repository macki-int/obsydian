`docker build [path_to_dockerfile]`
`docker build –no-cache –force-rm –tag=[image_tag] ./`    -preffered options


https://szkoladockera.pl/distroless-docker-images-vs-alpine-linux/
start dontainer ad deamon:
`docker run -it -d -p 8080:80 –name=[container_name] tag`
-i – interactive,
t – pseudo TTY,
-d – as daemon,
-p – allowconnect to the container  from out of host
Port – (here: container port 8080, host port 80). 
--name – container name,

/*Jeśli uruchomienie kontenera nie będzie możliwe, a błąd wskazuje na `docker.proxy` lub `docker-runc` oznacza to najprawdopodobniej brak linka symbolicznego w `/usr/libexec/docker`. Aplikacja odpytuje o plik `/usr/libexec/docker/docker-runc`, który nie istnieje. W takiej sytuacji należy dodać link symboliczny:
`ln -s /usr/libexec/docker/docker-runc-current /usr/libexec/docker/docker-runc`
A następnie dodać ścieżkę `/usr/libexec/docker/docker-runc` do zmiennej środowiskowej `$PATH`

`FROM`  baseImage //eg. `dockerfile alpine:3.14`
`RUN`  apt update && apt install python3 - exec command during create image
`COPY` my_script.py - from some path to containar destination
`ENTRYPOINT`  \ `CMD` ["python", "my_script.py"] - "start container"

`LABEL` maintainer="Info eg. version number"
#### **CMD**
vs
#### **ENTRYPOINT**


https://szkoladockera.pl/dockerfile-entrypoint-vs-cmd/
**EXEX** (<instruction> ["executable", "param1", "param2"])
FROM ubuntu:18.04
CMD ["/bin/ping", "localhost"]

**vs**

**SHELL** (<instruction> <command>)
FROM ubuntu:18.04
CMD ping localhost



