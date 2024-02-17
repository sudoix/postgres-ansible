# postgres-ansible

```
ansible-playbook -i inventory/db-servers.ini postgres.yml --become --become-method=sudo -t preinstall
```

```
ansible-playbook -i inventory/db-servers.ini postgres.yml --become --become-method=sudo -t postgres
```

```
ansible-playbook -i inventory/db-servers.ini postgres.yml --become --become-method=sudo -t haproxy
```

