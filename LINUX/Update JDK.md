sudo apt update && sudo apt upgrade -y

apt-cache search openjdk

*sudo apt-get install openjdk-18-jre -y*
sudo apt-get install openjdk-18-jdk -y

java --version

uninstall:
sudo apt-get autoremove openjdk-18-jre openjdk-18-jdk --purge -y