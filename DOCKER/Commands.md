
`docker container start my_container`
`docker container stop my_container`

`docker container run my_app`
`docker container kill my_container`

A flag with one dash is a shortcut for the full flag name.
 `-p` is short for the `--port` flag.
 
`docker ps -a` - prints a list of running containers
`docker logs --tail 100 <container ID>` - the latest 100 logs for your container
`docker images` - list of images

`docker container my_command`
`create` — Create a container from an image
`start` — Start an existing container
`run` — Create a new container and start it
`ls` — List running containers
`inspect` — See lots of info about a container
`logs` — Print logs
`stop` — Gracefully stop running container
`kill` —Stop main process in container abruptly
`rm`— Delete a stopped container

`docker image my_command`
`build` — Build an image
`push` — Push an image to a remote registry
`ls` — List images
`history` — See intermediate image info
`inspect` — See lots of info about an image, including the layers
`rm` — Delete an image

`docker version` — List info about your Docker Client and Server versions
`docker login` — Log in to a Docker registry
`docker system prune` — Delete all unused containers, unused networks, and dangling images

`docker container ls -a -s` — List running containers
`-a` is short for `-all`. List all containers (not just running ones)
`-s` is short for `--size`

`docker container create my_repo/my_image:my_tag`— Create a container from an image
`docker container run my_image` — Create a new container and start it
`docker container inspect my_container` — See lots of info about a container
`docker container logs my_container` — Print a container’s logs
`docker container logs --follow my_container` — Print live a container’s logs

`docker image history my_image` — Display an image’s intermediate images with sizes and how they were created
`docker image inspect my_image` — Show lots of details about your image

**docker container run -i -t -p 1000:8000 --rm my_image**
`-i` is short for `--interactive`. Keep STDIN open even if unattached.
`-t`is short for`--tty`. Allocates a pseudo that connects your terminal with the container’s STDIN and STDOUT.
`1000:8000` maps the Docker port 8000 to port 1000

`**docker image build -t my_repo/my_image:my_tag .**` — Build a Docker image named _my_image_ from the Dockerfile located at the specified path or URL. The `.` (period) at the end of the command tells Docker to build the image according to the Dockerfile in the current working directory

`**docker login**` — Log in to a Docker registry
`**docker image push my_repo/my_image:my_tag**` — Push an image to a registry

https://www.how2shout.com/linux/how-to-install-sudo-on-debian-or-ubuntu-linux/
https://www.fosslinux.com/49959/install-docker-on-debian.htm
systemctl status docker