sudo apt update && sudo apt upgrade
 
//sudo apt-get -y install postgresql 
sudo apt install postgresql postgresql-contrib

sudo systemctl status postgresql -  check status service
sudo systemctl stop postgresql - stop service
sudo systemctl start postgresql - start service

sudo passwd postgres  - set password

sudo su postgres 
psql 

createdb demodb
psql demodb
`\q` - quit

for connection info : `\conninfo`
for password : `\password` 
for roles : `\du` 
for database : `\l`
for relation : `\d`
for table : `\dt`

`createdb`