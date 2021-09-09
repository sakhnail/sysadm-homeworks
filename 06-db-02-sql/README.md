1. Команда запуска контейнера
```shell
docker run --rm --name pg-docker -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e POSTGRES_DB=pgtestdb -d -p 5432:5432 -v vol1:/var/lib/postgresql/data -v vol2:/var/lib/postgresql postgres:12
```
```shell
docker exec -it pg-docker psql -U postgres
```
2. Создал базу данных
![img.png](img.png)

Создал пользователя test-admin-user

![img_1.png](img_1.png)

Назначил права на базу test-bd test-admin-user

![img_3.png](img_3.png)

Список таблиц и прав на них

![img_4.png](img_4.png)
![img_5.png](img_5.png)

