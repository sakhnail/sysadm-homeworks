1. Собрал образ ES

![img_1.png](img_1.png)

запустил контейнер

```shell
docker run -p 9200:9200 --name es-home --memory="1g" -d elasticsearch
```
![img_2.png](img_2.png)

[Ссылка](https://hub.docker.com/repository/docker/sakhnail/elasticsearch) на репозиторий с образом

2. 