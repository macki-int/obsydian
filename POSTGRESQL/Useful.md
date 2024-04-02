`ps -ef | grep postgres`
`sudo pg_isready` - /var/run/postgresql:5432 - no response/accepting connections
pg_isready -h localhost -p 5432

sudo systemctl status postgresql
sudo systemctl is-enabled postgresql
sudo systemctl is-active postgresql


sudo apt-get update && sudo apt install postgresql

```
systemctl list-dependencies postgresql
```