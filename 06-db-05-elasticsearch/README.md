1. Собрал образ ES

![img_1.png](img_1.png)

[Dockerfile](https://github.com/sakhnail/sysadm-homeworks/blob/main/06-db-05-elasticsearch/Dockerfile)

запустил контейнер

```shell
docker run -p 9200:9200 --name es-home --memory="1g" -d elasticsearch
```
![img_5.png](img_5.png)

[Ссылка](https://hub.docker.com/repository/docker/sakhnail/elastic) на репозиторий с образом

2. Список индексов и статус

![img_8.png](img_8.png)

![img_7.png](img_7.png)

Статус <code>Yellow</code> потому что указано количество реплик, а так как это кластер, но с одним сервером, реплики невозможно создать, я так думаю.

Удаление индексов:

```shell
curl.exe -X DELETE "127.0.0.1:9200/ind-1?pretty" {/"acknowledged/" : true}
curl.exe -X DELETE "127.0.0.1:9200/ind-2?pretty" {/"acknowledged/" : true}
curl.exe -X DELETE "127.0.0.1:9200/ind-3?pretty" {/"acknowledged/" : true}
```

![img_9.png](img_9.png)

3. Создал каталог в snapshots в корневой директории ES.

![img_10.png](img_10.png)

Зарегистрировал репозиторий
![img_11.png](img_11.png)

![img_12.png](img_12.png)

Создал индекс test реплика 0, шард 1:

```shell
curl.exe -X PUT "127.0.0.1:9200/test?pretty" -H 'Content-Type: application/json' -d'
>> {
>> "settings":{
>> "number_of_shards": 1,
>> "number_of_replicas": 0
>> }
>> }
>> ' {\"acknowledged\" : true, \"shards_acknowledged\" : true, \"index\" : "test"}
```
Сделал снапшот: 

```shell
curl.exe -X PUT "127.0.0.1:9200/_snapshot/netology_backup/snapshot_test?wait_for_completion=true&pretty" {\"snapshot\" : {\"snapshot\" : "snapshot_test", \"uuid\" : "LvR3VmNES2CVUii8eAPi7Q", \"version_id\" : 7130399, \"version\" : "7.13.3", \"indices\" : ["test"], \"data_streams\" : [ ], \"include_global_state\" : true, \"state\" : "SUCCESS",\"start_time\" : "2021-10-03T13:09:57.575Z",\"start_time_in_millis\" : 1626613797575,\"end_time\" : "2021-10-03T13:09:57.575Z",\"end_time_in_millis\" : 1626613797575,\"duration_in_millis\" : 0,\"failures\" : [ ],\"shards\" : {\"total\" : 1,\"failed\" : 0,\"successful\" : 1},\"feature_states\" : [ ]}}
```

Список снапшотов:

![img_13.png](img_13.png)

Удаление индекса test

```shell
curl.exe -X DELETE "127.0.0.1:9200/test?pretty" {\"acknowledged\" : true}
```

Создание индекса test-2

![img_14.png](img_14.png)

Восстановление снапшота
```shell
curl.exe -X POST "127.0.0.1:9200/_snapshot/netology_backup/snapshot_test/_restore?pretty"{\"accepted\" : true}
```
Список индексов после восстановления

![img_15.png](img_15.png)

**Если честно, это самая непонятная для меня тема, я все делал по инструкциям и не знаю. на сколько правильно делал. 