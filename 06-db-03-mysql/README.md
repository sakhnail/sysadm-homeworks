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

3. Установил профилирование SET profiling = 1

![img_4.png](img_4.png)

Информация об engine в таблице БД test_db

![img_5.png](img_5.png)

Изменил engine на MyISAM

![img_6.png](img_6.png)

Отображение профайлера:

![img_7.png](img_7.png)

Изменение движка на InnoDB

![img_8.png](img_8.png)

Отображание профайлера

![img_9.png](img_9.png)

4. Файл my.cnf
