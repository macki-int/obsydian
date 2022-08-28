https://linuxhint.com/install-docker-ubuntu-22-04/

***Ctrl+Alt+T - open terminal***

sudo apt update

sudo apt upgrade

sudo apt install lsb-release ca-certificates apt-transport-https software-properties-common -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update

sudo apt install docker-ce

sudo systemctl status docker

***sudo docker run hello-world***

sudo docker ps -a