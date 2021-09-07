1. Команда запуска контейнера
```shell
docker run --rm --name pg-docker -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e POSTGRES_DB=pgtestdb -d -p 5432:5432 -v vol1:/var/lib/postgresql/data -v vol2:/var/lib/postgresql postgres:12
```
```shell
docker exec -it pg-docker psql -U postgres
```
2.