dpkg -l | grep postgresql

sudo cp -R /var/lib/postgresql /var/lib/postgresql_backup

sudo systemctl disable postgresql
sudo apt-get purge postgresql-16
sudo apt-get autoremove
sudo rm -rf /etc/postgresql
sudo rm -rf /var/lib/postgresql
sudo find / -iname "*postgres*" -exec rm -rf {} \;

|     |     |
| --- | --- |
|     |     |
