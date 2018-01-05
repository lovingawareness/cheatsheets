# postgresql cheatsheet

## Examples

### Get into the postgres psql interface

```
$ sudo -u postgres psql
[sudo] password for nick:
psql (9.5.10)
Type "help" for help.

postgres=#
```

### How to quit

```
postgres=# \q
```

### Getting help

```
postgres=# \?
```

### List all the tables in the `import` schema:

```
postgres=# \dt+ import.*
                         List of relations
 Schema |      Name      | Type  |  Owner   |  Size   | Description
--------+----------------+-------+----------+---------+-------------
 import | customer       | table | postgres | 7752 kB |
 import | friends        | table | postgres | 16 kB   |
 import | ticket_details | table | postgres | 27 MB   |
 import | ticket_history | table | postgres | 57 MB   |
(4 rows)
```

### Get the number of records in the `ticket_history` table found in the `import` schema

```
postgres=# SELECT COUNT(*) FROM import.ticket_history;
 count
--------
 161821
(1 row)
```

### Get a sample record from the `import.ticket_history` table

```
postgres=# SELECT * FROM import.ticket_history LIMIT 1;
 ticket_id |     action_date     |     comments      | time_spent |  action_name   | performed_by_csr | assigned_to_csr
-----------+---------------------+-------------------+------------+----------------+------------------+------------------
 8344603   | Jun 26 2017 10:28AM | Obsolete, closing | 0          | Manually Close | David Montgomery | David Montgomery
(1 row)
```

### Dump all databases to file

First, log in as the postgres management user:

```bash
sudo su postgres
```

Then, run this to dump all databases to file:

```bash
pg_dumpall > pgall.pgsql
```

### Load database dump into new PostgreSQL server on Mac

```bash
psql -f pgall.pgsql postgres
```

## References:

### Reference

1. [Tuning Your PostgreSQL Server](https://wiki.postgresql.org/wiki/Tuning_Your_PostgreSQL_Server)
1. [Official PostgreSQL 9.6.6 Documentation](https://www.postgresql.org/docs/9.6/static/index.html)

### Tutorials

1. [PostgreSQL Tutorial](http://www.postgresqltutorial.com/)
1. [Getting Started with PostgreSQL](https://www.ntu.edu.sg/home/ehchua/programming/sql/PostgreSQL_GetStarted.html)
1. [Official PostgreSQL 9.6 Tutorial](https://www.postgresql.org/docs/9.6/static/tutorial-start.html)
1. [pgfutter tool - Import CSV and JSON into PostgreSQL the easy way](https://github.com/lukasmartinelli/pgfutter)
1. [StackOverflow - Using pgfutter tool to import CSVs and create tables](https://stackoverflow.com/questions/21018256/can-i-automatically-create-a-table-in-postgresql-from-a-csv-file-with-headers/34882452#34882452)
