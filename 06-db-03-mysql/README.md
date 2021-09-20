1. Запустил контейнер:
```shell
docker run --name mysql-docker -e MYSQL_ROOT_PASSWORD=mysql -ti -d -p 3306:3306 -v vol_mysql:/etc/mysql/ -v c:\tmp\mysql:/tmp/ mysql:8.0
```
Восстановил БД из дампа:
```shell
mysql -p test_db < /tmp/test_dump.sql
```
Получил статус БД: 

![img.png](img.png)

Выввел количество записей с price > 300

![img_1.png](img_1.png)

2. Создал пользователя test в БД c паролем test-pass

![img_2.png](img_2.png)

![img_3.png](img_3.png)

3. 