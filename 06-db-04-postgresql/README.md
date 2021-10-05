1. Запустил контейнер с pg:
```shell
docker run --name pg-docker -e POSTGRES_PASSWORD=postgres -ti -d -p 5432:5432 -v vol_postgres:/var/lib/postgresql/data postgres:13
```
запустил psql

```shell
docker exec -it pg-docker psql -U postgres -W
```
список бд:

![img.png](img.png)

вывод списка таблиц в postgres и описания (я поставил на конце S, так как по \dt он мне не выдал список таблиц, видимо, потому что пользовательских таблиц нет)

![img_1.png](img_1.png)

![img_2.png](img_2.png)

выход из psql
```shell
postgres=# \q
```
2. Восстановил базу из дампа:
```shell
psql -U postgres -f /var/lib/postgresql/data/test_dump.sql test_database;
```
![img_3.png](img_3.png)

![img_4.png](img_4.png)

Вывод ANALYZE:

![img_5.png](img_5.png)

Столбец orders:

![img_6.png](img_6.png)

3. Обновил имя базы: 
```shell
 alter table orders rename to orders_ex;
```
Создал новые таблицы: 
сначала я хотел сделать так: 
```shell
 create table orders (like orders_ex including all) partition by range(price);
```
но получил ошибку:

![img_7.png](img_7.png)

пришлось деать так: 

```shell
create table orders (id integer, title varchar(80), price integer) partition by range(price);
```
![img_8.png](img_8.png)

затем создал 2 партиции: 
правда, со второй ошибку допустил,
![img_9.png](img_9.png)

но потом поправил и зарузил данные в таблицу orders:

![img_10.png](img_10.png)

результат по таблицам orders_1 и orders_2

![img_11.png](img_11.png)

4. Создал [дамп](https://github.com/sakhnail/sysadm-homeworks/blob/main/06-db-04-postgresql/test_dump_210921.sql) бд test_database

![img_12.png](img_12.png)

![img_13.png](img_13.png)

Добавил бы UNIQUE при создании таблицы

```shell
CREATE TABLE public.orders (
    id integer NOT NULL,
    title character varying(80) UNIQUE,
    price integer DEFAULT 0
);
```