# Нow import database from production

Mysql:
 
```bash
ssh -C {ssh.user}@{remote_host} \
'mysqldump -u {remote_dbuser} --password={remote_dbpassword} {remote_dbname} | bzip2 -c' \ 
| bunzip2 -dc | mysql -u {local_dbuser} --password={local_dbpassword} -D {local_dbname}
```


Postgres:

```bash
ssh -C {ssh.user}@{remote_host} \
'PGPASSWORD={remote_dbpassword} pg_dump -U{remote_dbuser} {remote_dbname} | bzip2 -c' \ 
| bunzip2 -dc | PGPASSWORD={local_dbpassword} psql -U{local_dbuser} {local_dbname}
```
