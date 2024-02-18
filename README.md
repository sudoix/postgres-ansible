# postgres-ansible

### Setting up a High Availability (HA) cluster for PostgreSQL with Ansible

```
ansible-playbook -i inventory/db-servers.ini postgres.yml --become --become-method=sudo -t preinstall
```

```
ansible-playbook -i inventory/db-servers.ini postgres.yml --become --become-method=sudo -t postgres
```

```
ansible-playbook -i inventory/db-servers.ini postgres.yml --become --become-method=sudo -t haproxy
```

List your databases:

```
patronictl -c /etc/patroni.yml list
```

Connect to databases:

```
psql -h KEEPALIVE_IP -p 5000 -U postgres
Password for user postgres:


psql (14.9 (Ubuntu 14.9-0ubuntu0.22.04.1))
Type "help" for help.

postgres=# \dt;
Did not find any relations.
postgres=# \l
                                  List of databases
   Name    |  Owner   | Encoding |   Collate   |    Ctype    |   Access privileges
-----------+----------+----------+-------------+-------------+-----------------------
 postgres  | postgres | UTF8     | en_US.UTF-8 | en_US.UTF-8 |
 template0 | postgres | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =c/postgres          +
           |          |          |             |             | postgres=CTc/postgres
 template1 | postgres | UTF8     | en_US.UTF-8 | en_US.UTF-8 | =c/postgres          +
           |          |          |             |             | postgres=CTc/postgres

```


References:

https://medium.com/@murat.bilal/setting-up-a-postgresql-ha-cluster-0a4348fca444