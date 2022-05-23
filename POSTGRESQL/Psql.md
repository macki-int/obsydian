`\q` - quit

for connection info : `\conninfo`
for password : `\password` 
for roles : `\du` 
for database : `\l`
for relation : `\d`
for table : `\dt` or `\dt+`


```sql
\c demo_datavase user_name
```

```sql
SELECT * FROM pg_catalog.pg_tables 
WHERE schemaname != 'pg_catalog' 
AND schemaname != 'information_schema';
```