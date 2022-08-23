**Script to backup postgresql database with cronjob (one per day)**
```
su postgres
```
```bash
#!/bin/bash
cd /path/to/backup/
pg_dump dbname > dbname.$(date.%F).dat.sql
tar -cf dbname.$(date.%F).tar dbname.$(date.%F).dat.sql
gzip dbname.$(date.%F).tar
rm -f dbname.$(date.%F).dat.sql
```
```
crontab -e

# It will take the backup always at 01 AM
# PostgreSQL backup
0 1 * * *      /path/to/script.sh
```
or 
```bash
#!/bin/bash
BACKUP_DIR="/data/psql-db-backup/"
FILE_NAME=$BACKUP_DIR`date +%d-%m-%Y-%I-%M-%S-%p`.sql
pg_dump -U db_user db_name > $FILE_NAME
```
```
crontab -e

# It will take the backup past every 3rd hour
# PostgreSQL backup
0 */3 * * * /data/postgresql-backup.sh
```