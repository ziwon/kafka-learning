Docker for Mac >= 1.12, Linux, Docker for Windows 10:

    docker run --rm -it \
               -p 2181:2181 -p 3030:3030 -p 8081:8081 \
               -p 8082:8082 -p 8083:8083 -p 9092:9092 \
               -e ADV_HOST=127.0.0.1 \
               landoop/fast-data-dev

Docker toolbox:

    docker run --rm -it \
              -p 2181:2181 -p 3030:3030 -p 8081:8081 \
              -p 8082:8082 -p 8083:8083 -p 9092:9092 \
              -e ADV_HOST=192.168.99.100 \
              landoop/fast-data-dev

Kafka command lines tools:

    docker run --rm -it --net=host landoop/fast-data-dev bash


Results:

    docker run --rm -it \
               -p 2181:2181 -p 3030:3030 -p 8081:8081 \
               -p 8082:8082 -p 8083:8083 -p 9092:9092 \
               -e ADV_HOST=127.0.0.1 \
               landoop/fast-data-dev
    Setting advertised host to 127.0.0.1.
    Operating system RAM available is 1755 MiB, which is less than the lowest
    recommended of 5120 MiB. Your system performance may be seriously impacted.
    Starting services.
    This is landoop’s fast-data-dev. Kafka 0.10.2.1, Confluent OSS 3.2.1.
    You may visit http://127.0.0.1:3030 in about a minute.
    2017-05-20 02:23:39,015 CRIT Supervisor running as root (no user in config file)
    2017-05-20 02:23:39,015 WARN No file matches via include "/etc/supervisord.d/*.conf"
    2017-05-20 02:23:39,020 INFO supervisord started with pid 6
    2017-05-20 02:23:40,028 INFO spawned: 'sample-data' with pid 94
    2017-05-20 02:23:40,032 INFO spawned: 'zookeeper' with pid 95
    2017-05-20 02:23:40,041 INFO spawned: 'caddy' with pid 97
    2017-05-20 02:23:40,044 INFO spawned: 'broker' with pid 99
    2017-05-20 02:23:40,047 INFO spawned: 'smoke-tests' with pid 103
    2017-05-20 02:23:40,050 INFO spawned: 'connect-distributed' with pid 106
    2017-05-20 02:23:40,053 INFO spawned: 'logs-to-kafka' with pid 107
    2017-05-20 02:23:40,057 INFO spawned: 'schema-registry' with pid 109
    2017-05-20 02:23:40,060 INFO spawned: 'rest-proxy' with pid 110
    2017-05-20 02:23:41,112 INFO success: sample-data entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,112 INFO success: zookeeper entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,113 INFO success: caddy entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,113 INFO success: broker entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,113 INFO success: smoke-tests entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,113 INFO success: connect-distributed entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,113 INFO success: logs-to-kafka entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,114 INFO success: schema-registry entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:41,114 INFO success: rest-proxy entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:42,757 INFO exited: schema-registry (exit status 1; not expected)
    2017-05-20 02:23:42,765 INFO spawned: 'schema-registry' with pid 291
    2017-05-20 02:23:43,055 INFO exited: rest-proxy (exit status 1; not expected)
    2017-05-20 02:23:43,537 INFO spawned: 'rest-proxy' with pid 330
    2017-05-20 02:23:44,147 INFO success: schema-registry entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
    2017-05-20 02:23:44,562 INFO success: rest-proxy entered RUNNING state, process has stayed up for > than 1 seconds (startsecs)
