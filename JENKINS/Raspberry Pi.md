*Install*
sudo apt update 
sudo apt upgrade

java --version

`curl https://pkg.jenkins.io/debian/jenkins.io.key | gpg --dearmor | sudo tee /usr/share/keyrings/jenkins-archive-keyring.gpg >/dev/null`
`
sudo nano /etc/apt/sources.list.d/jenkins.list  - add  text:
```
deb [signed-by=/usr/share/keyrings/jenkins-archive-keyring.gpg] https://pkg.jenkins.io/debian binary/
```

sudo apt update
sudo apt install jenkins

*Unlocking Jenkina*
hostname -I

sudo cat /var/lib/jenkins/secrets/initialAdminPassword - view passwort to unlock

go to Jenkins
IP_address:8080

insert password

install suggested plugins

*Controlling*
sudo systemctl status jenkins
sudo systemctl stop jenkins
sudo systemctl disable jenkins
sudo systemctl enable jenkins


https://pimylifeup.com/jenkins-raspberry-pi/