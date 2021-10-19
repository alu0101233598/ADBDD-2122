```bash
usuario@ubuntu:~$ sudo apt install -y postgresql

Reading package lists... Done                                                       
Building dependency tree                                                            
Reading state information... Done                                                   
The following additional packages will be installed:                                                                                                                    
  libllvm10 libpq5 libsensors-config libsensors5 postgresql-12 postgresql-client-12 postgresql-client-common postgresql-common ssl-cert sysstat
Suggested packages:                                                                 
  lm-sensors postgresql-doc postgresql-doc-12 libjson-perl openssl-blacklist isag
The following NEW packages will be installed:                               
  libllvm10 libpq5 libsensors-config libsensors5 postgresql postgresql-12 postgresql-client-12 postgresql-client-common postgresql-common ssl-cert sysstat
0 upgraded, 11 newly installed, 0 to remove and 57 not upgraded.
Need to get 30.6 MB of archives.                                                    
After this operation, 122 MB of additional disk space will be used.
Get:1 http://es.archive.ubuntu.com/ubuntu focal/main amd64 libllvm10 amd64 1:10.0.0-4ubuntu1 [15.3 MB]
Get:2 http://es.archive.ubuntu.com/ubuntu focal-updates/main amd64 libpq5 amd64 12.8-0ubuntu0.20.04.1 [116 kB]
...
Success. You can now start the database server using:

    pg_ctlcluster 12 main start
```

```bash
postgres@ubuntu:/home/usuario$ service postgresql status
● postgresql.service - PostgreSQL RDBMS
     Loaded: loaded (/lib/systemd/system/postgresql.service; enabled; vendor preset: enabled)
     Active: active (exited) since Wed 2021-10-13 09:10:45 UTC; 7min ago
   Main PID: 5297 (code=exited, status=0/SUCCESS)
      Tasks: 0 (limit: 4613)
     Memory: 0B
     CGroup: /system.slice/postgresql.service
```

```bash
postgres@ubuntu:/home/usuario$ psql
psql (12.8 (Ubuntu 12.8-0ubuntu0.20.04.1))
Type "help" for help.

postgres=# CREATE USER alu0101233598;
CREATE ROLE
postgres=# ALTER ROLE alu0101233598 WITH PASSWORD 'adbdd2122';
ALTER ROLE
```

```bash
postgres=# CREATE DATABASE pract1;
CREATE DATABASE
```

```sql
usuario@ubuntu:~$ psql -U alu0101233598 -h 127.0.0.1 pract1
Password for user alu0101233598: 
psql (12.8 (Ubuntu 12.8-0ubuntu0.20.04.1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

pract1=> \dt
Did not find any relations.
pract1=> create table usuarios (
pract1(>   nombre varchar(30),
pract1(>   clave varchar(10)
pract1(>  );
CREATE TABLE
pract1=> insert into usuarios (nombre, clave) values ('Isa','asdf');
INSERT 0 1
pract1=>  insert into usuarios (nombre, clave) values ('Pablo','jfx344');
INSERT 0 1
pract1=>  insert into usuarios (nombre, clave) values ('Ana','tru3fal');
INSERT 0 1
pract1=> \dt
             List of relations
 Schema |   Name   | Type  |     Owner     
--------+----------+-------+---------------
 public | usuarios | table | alu0101233598
(1 row)

pract1=> SELECT * FROM usuarios;
 nombre |  clave  
--------+---------
 Isa    | asdf
 Pablo  | jfx344
 Ana    | tru3fal
(3 rows)
```