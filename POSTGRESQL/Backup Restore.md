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
crontab -e -u postgres

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


Back up or restore the TeamWorks database from the command line

## Backup PostgreSQL
1.  Shut down the PostgreSQL service
2.  Run the following command
	`PostgreSQLdump -u root -p TeamWorks >/backupdir/TeamWorksback.sql`
    *This creates a file named TeamWorksback that can be used to restore the database*
3.  Restart PostgreSQL.
    

## Restoring PostgreSQL from a Backup File
1.  (Optional) If a TeamWorks table does not exist,  create it  
    1.  Log in to PostgreSQL using the following command:
        `PostgreSQL -p`
    2.  Create the database using the following command:
        `create database TeamWorks;`
    
2.  When a TeamWorks table exists on the location
    1.  Quit PostgreSQL
    2.  Run the following command
        `PostgreSQL -p TeamWorks < /backupdir/TeamWorks-back.sql`
	    *This completes the restore of the TeamWorks database and its associated tables*


Restore
`psql -U username -d database_name -f objects.sql`
`psql -U postgres -d wims -f wims.sql`

Backup all databases (*as postgres user*) 
*ssh vaio@192.168.0.60*
*scp xxxx.sql xxxx@ip.ip.ip.ip:/home/xxxx/xxxx.sql*

`pg_dumpall -U postgres > c:\\pgbackup\\all.sql`
`pg_dump -U postgres -d wims -f wims.sql`


https://www.postgresqltutorial.com/