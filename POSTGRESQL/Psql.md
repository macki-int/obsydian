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


```sql
SELECT setval('payments_id_seq', 21, true); - next value will 22
```
Option

Description

-a  
--echo-all

Print all nonempty input lines to standard output as they are read. This is equivalent to setting the variable ECHO to all.

-A  
--no-align

Switches to unaligned output mode.

-c command  
--command=command

Specifies that psql is to execute one command string, command, and then exit. This is useful in shell scripts. Start-up files (psqlrc and ~/.psqlrc) are ignored with this option.

-d dbname  
--dbname=dbname_

Secifies the name of the database to connect to. This is equivalent to specifying dbname as the first non-option argument on the command line.

-e  
--echo-queries

Copy all SQL commands sent to the server to standard output as well. This is equivalent to setting the variable ECHO to queries.

-E  
--echo-hidden

Use the file filename as the source of commands instead of reading commands interactively. After the file is processed, psql terminates. This is in many ways equivalent to the meta-command \i.

-F separator  
--field-separator=separator

Use separator as the field separator for unaligned output. This is equivalent to \pset fieldsep or \f.

-h hostname  
--host=hostname_

Specifies the host name of the machine on which the server is running. If the value begins with a slash, it is used as the directory for the Unix-domain socket.

-H  
--html

Turn on HTML tabular output. This is equivalent to \pset format html or the \H command.

-l  
--list

List all available databases, then exit. Other non-connection options are ignored. This is similar to the meta-command \list.

-L filename  
--log-file=filename

Write all query output into file filename, in addition to the normal output destination.

-n  
--no-readline

Do not use Readline for line editing and do not use the command history. This can be useful to turn off tab expansion when cutting and pasting.

-o filename  
--output=filename

Put all query output into file filename. This is equivalent to the command \o.

-p port  
--port=port_

Specifies the TCP port or the local Unix-domain socket file extension on which the server is listening for connections. Defaults to the value of the PGPORT environment variable or, if not set, to the port specified at compile time, usually 5432.

-P assignment  
--pset=assignment

Specifies printing options, in the style of \pset. Note that here you have to separate name and value with an equal sign instead of space. For example, to set the output format to LaTeX, you could write -P format=latex.

-q  
--quiet

Specifies that psql should do its work quietly. By default, it prints welcome messages and various informational output. If this option is used, none of this happens. This is useful with the -c option. This is equivalent to setting the variable QUIET to on.

-R separator  
--record-separator=separator

Use separator as the record separator for unaligned output.

-S  
--single-line

Runs in single-line mode where a newline terminates an SQL command, as a semicolon does.

-t  
--tuples-only

Turnoff printing of column names and result row count footers, etc.

-T table_options  
--table-attr=table_options

Specifies options to be placed within the HTML table tag. See \pset for details.

-U username  
--username=username_

Connect to the database as the user username instead of the default. (You must have permission to do so, of course.)

-v assignment  
--set=assignment  
--variable=assignment

Perform a variable assignment, like the \set meta-command. Note that you must separate name and value if any, by an equal sign on the command line.

-V  
--version

Print the psql version and exit.

-w  
--no-password_

Never issue a password prompt. If the server requires password authentication and a password is not available by other means such as a .pgpass file, the connection attempt will fail. This option can be useful in batch jobs and scripts where no user is present to enter a password.

-W  
--password_

Force psql to prompt for a password before connecting to a database.

-x  
--expanded

Turn on the expanded table formatting mode.

-X,  
--no-psqlrc

Do not read the start-up file.

-z  
--field-separator-zero

Set the field separator for unaligned output to a zero byte.

-0  
--record-separator-zero

Set the record separator for unaligned output to a zero byte. This is useful for interfacing, for example, with xargs -0.

-1  
--single-transaction

When psql executes a script with the -f option, adding this option wraps BEGIN/COMMIT around the script to execute it as a single transaction. This ensures that either all the commands complete successfully, or no changes are applied.

-?  
--help

Show help about psql command line arguments and exit.