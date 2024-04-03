https://linuxize.com/post/how-to-install-postgresql-on-debian-10/

sudo apt update && sudo apt upgrade
 
//sudo apt-get -y install postgresql 
sudo apt install postgresql postgresql-contrib

sudo systemctl status postgresql -  check status service
sudo systemctl stop postgresql - stop service
sudo systemctl start postgresql - start service

sudo passwd postgres  - set password

sudo su postgres 
psql 

create database demodb
psql demodb

```

CREATE DATABASE hr 
WITH 
   ENCODING = 'UTF8'
   OWNER = hr
   CONNECTION LIMIT = 100;
   
`create database`

create user user_name with encrypted password 'mypassword';
grant all privileges on database sample_db to user_name;


# ERROR: new encoding (UTF8) is incompatible
UPDATE pg_database SET datistemplate = FALSE WHERE datname = 'template1';
DROP DATABASE template1;
CREATE DATABASE template1 WITH TEMPLATE = template0 ENCODING = 'UNICODE';
UPDATE pg_database SET datistemplate = TRUE WHERE datname = 'template1'; - set as actually template
\c template1 - switch to template1
VACUUM FREEZE;

https://wiki.debian.org/PostgreSql
apt install postgresql postgresql-client
apt search postgresql

pg_lsclusters

psql --version
```sql
SELECT version();
```


https://www.commandprompt.com/education/how-to-install-and-setup-postgresql-on-debian-12/
https://docs.percona.com/postgresql/16/major-upgrade.html