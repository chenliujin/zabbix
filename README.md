

# 
- 自动发现和自动注册

# Metrics
- CPU
- Memory
- Network
- Disk free space
- Disk I/O
- HTTP
- TCP


```
docker run \
        -d \
        --name zabbix \
        --restart always \
        -p 8082:80 \
        -p 10051:10051 \
        -v /etc/localtime:/etc/localtime:ro \
        --link zabbix-db:zabbix.db \
        --env="ZS_DBHost=zabbix.db" \
        --env="ZS_DBUser=zabbix" \
        --env="ZS_DBPassword=zabbix" \
        monitoringartist/zabbix-xxl:3.2.7
```


```
docker run \
        -d \
        --name zabbix-db \
        --restart always \
        -v /backups:/backups \
        -v /etc/localtime:/etc/localtime:ro \
        --env="MARIADB_USER=zabbix" \
        --env="MARIADB_PASS=zabbix" \
        monitoringartist/zabbix-db-mariadb
```
