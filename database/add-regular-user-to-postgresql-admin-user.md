Login using postgres user:
`sudo -u postgres psql`

Run this command:
`CREATE USER <username>`
`CREATE DATABASE <username>`
`ALTER ROLE <username> WITH SUPERUSER;`

Exit postgres shell:

`\q`

Open /etc/postgresql/<version>/main/pg_hba.conf files and add this below postgres user
```
...
local   all             postgres                                peer
local   all             <username>                              peer
```
