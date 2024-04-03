`ps -ef | grep postgres`
`sudo pg_isready` - /var/run/postgresql:5432 - no response/accepting connections
pg_isready -h localhost -p 5432

sudo systemctl status postgresql
sudo systemctl is-enabled postgresql
sudo systemctl is-active postgresql


sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update && sudo apt install postgresql

```
systemctl list-dependencies postgresql
```


Create an account where the user can create databases:
```sql
CREATE USER manuel WITH PASSWORD 'jw8s0F4' CREATEDB;
```

To change/modify the database owner, users must follow the below syntax:
```sql
ALTER DATABASE db_name
OWNER TO new_owner_name;
```