<p>1. Подходящие типы СУБД для каждой сущности:</p>

- Электронные чеки в json виде: думаю, что можно будет использовать MongoDB, так как по сути чеки - это документ
- Склады и автомобильные дороги для логистической компании: если это просто справочник, то можно использовать MySQL, PostgreSQL, MSSQL
- Генеалогические деревья - подойдёт NoSQL БД иерархической модели так как имеет аналогичную древовидную структуру, где присутствует связь родитель - потомок
- Кэш идентификаторов клиентов с ограниченным временем жизни для движка аутенфикации - ключ-значение, например, Redis, такое решение позволяет работать с кэш-данными и очищать их
- Отношения клиент-покупка для интернет-магазина - MySQL, PostgreSQL, MSSQL, любая реляционная база, так как будет использоваться более сложная схема связей

<p>2. </p>

| Пункт        | CAP           | PACELC  |
| ------------- |:-------------:| -----:|
| Данные записываются на все узлы с задержкой до часа (асинхронная запись)      | CA | EL-PC |
| При сетевых сбоях, система может разделиться на 2 раздельных кластера      | AP      |   PA-EL |
| Система может не прислать корректный ответ или сбросить соединение | CP      |    PA-EC |

<p>3. BASE и ACID сочетаться не могут. По ACID - данные согласованные, а по BASE - могут быть неверные, следовательно они противоречат друг другу.</p>
<p>4. Наверно, это будет Redis</p>
<p>Минусы Redis:</p>

- Redis хранит все в памяти, поэтому требуются достаточные ресурсы оперативной памяти
- У Redis нет языка запроса, как, например, SQL
- Redis предлагает только базовую безопасность (с точки зрения прав доступа) на уровне экземпляра
- Экземпляр Redis не масштабируется. Он работает только на одном ядре процессора в однопоточном режиме. Распределение и сегментирование осуществляется на стороне клиента (т. е. разработчик должен позаботиться об этом самостоятельно)