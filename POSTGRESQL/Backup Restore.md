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

Backup all databases
`pg_dumpall -U postgres > c:\\pgbackup\\all.sql`
`pg_dump -U postgres -d wims -f wims.sql`


https://www.postgresqltutorial.com/