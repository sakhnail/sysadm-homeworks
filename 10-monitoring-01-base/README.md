1. Минимальный набор метрик для вывода в мониторинг могут быть следующие:

    <p>Метрики оценки работоспособности оборудования:</p>
   
   * Нагрузка ЦПУ за 1,5,15 минут (CPU LA) - Так как вычисления загружают ЦПУ, данная метрика обязательна
   * IOPS - Анализ дисков, на которых сохраняется отчет 
   * inodes - Анализ дисков, на которых сохраняется отчет 
   * IOwait - Анализ дисков, на которых сохраняется отчет 
   * RAM - Анализ нагрузки RAM

    Метрики оценки работоспособности ПО:
   * Количество успешных и неуспешных ответов http-сервера - так как взаимодействие с платформой осуществляется по http, то нам важно знать успешность ответов.
   * Net traffic - Анализ нашего трафика
   * Доступность страницы приложения, открытие страницы (код 200)
   * Если ПО использует какие-то службы или само является службой, то поставить на мониторинг работоспособность данной службы
   * Количество сессий
   * Мониторинг БД
   
2. Можно предложить следующие метрики:
   * Время формирования отчета, можно разбить на несколько метрик: среднее время, а так же минимальное и максимальное время
   * Количество ошибок при формировании отчетов, точнее количество отчетов с ошибкой, завершившихся неудачно
   * Доступность приложения в разрезе времени (отклик на работоспособность)

3. Чтобы разработчики получили доступ к ошибкам и алертам можно организовать обычные текстовые логи, на общем ресурсе. Это самое простое. Или использовать ELK предоставить доступ в Кибану для разработчиков.
4. 
