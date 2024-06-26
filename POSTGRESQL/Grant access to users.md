**1. Grant CONNECT to the database:**
```
GRANT CONNECT ON DATABASE database_name TO username;
```
**2. Grant USAGE on schema:**
```
GRANT USAGE ON SCHEMA schema_name TO username;
```
**3. Grant on all tables for DML statements: SELECT, INSERT, UPDATE, DELETE:**
```
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA schema_name TO username;
```
**4. Grant all privileges on all tables in the schema:**
```
GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA schema_name TO username;
```
**5. Grant all privileges on all sequences in the schema:**
```
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA schema_name TO username;
```
**6. Grant all privileges on the database:**
```
GRANT ALL PRIVILEGES ON DATABASE database_name TO username;
```
**7. Grant permission to create database**:
```
ALTER USER username CREATEDB;
```
**8. Make a user superuser**:
```
ALTER USER myuser WITH SUPERUSER;
```
**9. Remove superuser status**:
```
ALTER USER username WITH NOSUPERUSER;
```

Those statements above only affect the current existing tables. To apply to newly created tables, you need to use alter default. For example:

```
ALTER DEFAULT PRIVILEGES
FOR USER username
IN SCHEMA schema_name
GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO username;
```