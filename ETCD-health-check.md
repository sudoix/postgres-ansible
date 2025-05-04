
# Adjust with your IPs






root@db-1:~# docker exec etcd0 /usr/local/bin/etcdctl   --endpoints=http://192.168.2.158:2379,http://192.168.2.31:2379,http://192.168.2.52:2379   member list
9f650397a300a2f0, started, etcd2, http://192.168.2.52:2380, http://192.168.2.52:2379,http://192.168.2.52:4001, false
a7e7e68eba331979, started, etcd0, http://192.168.2.158:2380, http://192.168.2.158:2379,http://192.168.2.158:4001, false
ac4876bbd924ea23, started, etcd1, http://192.168.2.31:2380, http://192.168.2.31:2379,http://192.168.2.31:4001, false



root@db-1:~# docker exec etcd0 /usr/local/bin/etcdctl \
  --endpoints=http://192.168.2.158:2379,http://192.168.2.31:2379,http://192.168.2.52:2379 \
  endpoint status --write-out=table
+---------------------------+------------------+---------+---------+-----------+------------+-----------+------------+--------------------+--------+
|         ENDPOINT          |        ID        | VERSION | DB SIZE | IS LEADER | IS LEARNER | RAFT TERM | RAFT INDEX | RAFT APPLIED INDEX | ERRORS |
+---------------------------+------------------+---------+---------+-----------+------------+-----------+------------+--------------------+--------+
| http://192.168.2.158:2379 | a7e7e68eba331979 |  3.5.17 |   20 kB |     false |      false |         2 |       6460 |               6460 |        |
|  http://192.168.2.31:2379 | ac4876bbd924ea23 |  3.5.17 |   20 kB |      true |      false |         2 |       6460 |               6460 |        |
|  http://192.168.2.52:2379 | 9f650397a300a2f0 |  3.5.17 |   20 kB |     false |      false |         2 |       6460 |               6460 |        |
+---------------------------+------------------+---------+---------+-----------+------------+-----------+------------+--------------------+--------+





root@db-1:~# docker exec etcd0 /usr/local/bin/etcdctl \
  --endpoints=http://192.168.2.158:2379,http://192.168.2.31:2379,http://192.168.2.52:2379 \
  endpoint health
http://192.168.2.31:2379 is healthy: successfully committed proposal: took = 3.881633ms
http://192.168.2.158:2379 is healthy: successfully committed proposal: took = 3.647308ms
http://192.168.2.52:2379 is healthy: successfully committed proposal: took = 3.610448ms