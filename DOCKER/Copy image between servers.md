docker save -o /home/usernsme/your_image.tar your_image_name

ls -lah /home/username/your_image.tar

rsync -avz /home/username/your_image.tar username@remote_server_ip_address:destination_directory

docker load -i your_image.tar 

docker images