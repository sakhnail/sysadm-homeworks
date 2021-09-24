1. Собрал образ ES

![img_1.png](img_1.png)

[Dockerfile](https://github.com/sakhnail/sysadm-homeworks/blob/main/06-db-05-elasticsearch/Dockerfile)

запустил контейнер

```shell
docker run -p 9200:9200 --name es-home --memory="1g" -d elasticsearch
```
![img_2.png](img_2.png)

[Ссылка](https://hub.docker.com/repository/docker/sakhnail/elasticsearch) на репозиторий с образом

2. 