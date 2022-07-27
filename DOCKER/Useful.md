docker run -d --restart always -p port_out:port_in dir/image:tag - *always start this image*
docker logs --follow container_id - show live logs
docker stats - show docker status

docker run --rm -it --network host <image_name> - *ustawienie loopback on host address*

docker build . -t  <image_name>:<tag_name>
docker run -d --rm -it --network host <image_name>:<tag_name>

docker update --restart=always <container_id>

GET /users?sort_by=asc(email)
