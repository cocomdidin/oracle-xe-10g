cocomdidin/oracle-xe-10g
====================

(based on the work done by Wei-Ming Wu <wnameless@gmail.com> on
[wnameless/docker-oracle-xe-11g](https://github.com/wnameless/docker-oracle-xe-11g)

Oracle Express Edition 10g Release 2 (10.2.0.1) 32-bit on Debian:jessie.

**The default characterset is ZHS16GBK and timezone is Asia/Jakarta.**


### Installation
```
docker pull cocomdidin/oracle-xe-10g
```

Run with 22, 1521, 8080 ports opened and volume mounted:
```
docker run --name oracle-xe-10g -d -p 49160:22 -p 1521:1521 -p 49162:8080  --mount source=oracle_xe_10g_vol,target=/usr/lib/oracle -e ORACLE_ALLOW_REMOTE=true   --restart=always cocomdidin/oracle-xe-10g:latest
```

The volume path on server is /var/lib/docker/volumes/oracle_xe_10g_vol

If the container restart or redeployed, the data is still in the volume. 

Connect database with following setting:
```
hostname: localhost
port: 1521
sid: xe
username: system
password: oracle
```

For example, connect to database with sqlplus:
```
sqlplus system/oracle@localhost:1521/xe
```

Password for SYS & SYSTEM
```
oracle
```

Login by SSH
```
ssh root@localhost -p 49160
password: admin
```

Login to web administrator on a browser:
```
http://localhost:49162/apex
```
