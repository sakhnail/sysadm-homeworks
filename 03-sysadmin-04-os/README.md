<p>1. Установил node_exporter, добавил его в автозагрузку</p>
<img src="../03-sysadmin-04-os/img/1_1q.JPG">
<p>2. То что выводится у меня в /metrics по умолчанию:</p> 
<p><img src="../03-sysadmin-04-os/img/1_2q.JPG"></p>
<p>Я бы, наверно использовал: </p>
<li>node_cpu_seconds_total</li>
<li>node_pressure_cpu_waiting_seconds_total</li>
<li>node_memory_MemAvailable_bytes</li>
<li>node_memory_MemFree_bytes</li>
<li>node_memory_SwapCached_bytes</li>
<li>node_memory_SwapFree_bytes</li>
<li>node_disk_read_time_seconds_total</li>
<li>node_disk_write_time_seconds_total</li>
<li>node_disk_io_time_seconds_total</li>
<li>smartmon_device_active</li>
<li>node_network_receive_drop_total</li>
<li>node_network_receive_errs</li>
<li>node_network_up</li>

<p>3. Netdata собирает такие метрики как     
    <li>cpu - Общая загрузка ЦП (все ядра). 100% здесь означает отсутствие простоя процессора.</li>
    <li>load - Текущая загрузка системы, то есть количество процессов, использующих ЦП или ожидающих системных ресурсов (обычно ЦП и диск).</li>
    <li>disk - Всего дисковых операций ввода-вывода для всех физических дисков.</li>
    <li>ram - Использование системной оперативной памяти (т.е. физической памяти).</li>
    <li>swap - Использование памяти подкачки системы.</li>
    <li>network - Общая пропускная способность всех физических сетевых интерфейсов, однако, здесь не учитываются VPN, сетевые мосты и т.п.</li>
    <li>processes - Системные процессы. Запущенные процессы в ЦП и заблокированые процессы.</li>
    <li>idlejitter</li>
    <li>interrupts - Общее количество прерываний ЦП.</li>
    <li>softirqs - анализируется для каждого ядра процессора.</li>
    <li>softnet - Статистика для CPU SoftIRQ, связанных с работой приема сети.</li>
    <li>entropy</li>
    <li>uptime</li>
    <li>ipc semaphores</li>
    <li>ipc shared memory</li>
<img src="../03-sysadmin-04-os/img/3q.JPG">
</p>
<p>4. Да, при помощи <code>dmesg</code> можно понять, что систему запущена на виртуальной машине, о чем будут свидетельствовать, например, такие сообщения: 
<p><code> hv_balloon: Max. dynamic memory size: 1024 MB</code></p>
<img src="../03-sysadmin-04-os/img/4q.JPG"></p>
<p>5. По-умолчанию fs.nr_open настроен на открытие 1048576 файлов</p>
<img src="../03-sysadmin-04-os/img/5q.JPG">
<p><code>ulimit -n 165635</code> увеличивает это значение, но как я понял временно до перезагрузки</p>
<img src="../03-sysadmin-04-os/img/5_1q.JPG">
<p>6. Сделал <code>unshare -f --pid --mount-proc sleep 1h</code>. Узнал его PID <code>ps auxf | grep sleep</code>. Зашел в этот аншеренный процесс <code>nsenter --target 70439 --pid --mount</code> (где 70439 это pid изолированного процесса). В нем уже сделал <code>ps aux</code></p>
<p><img src="../03-sysadmin-04-os/img/6q.JPG"></p>
<p>7. <code>:(){ :|:&amp; };:</code> это форк бомба, которая вызывает bash, который вызывает себя и так далее. При вызове <code>dmesg</code> можно увидеть, что <code>cgroup</code> помог стабилизации системы</p>
<img src="../03-sysadmin-04-os/img/7q.JPG"">
<p> чтобы изменить число процессов, которое можно создать в сессии надо изменить <code>DefaultTasksMax</code></p>
<p><img src="../03-sysadmin-04-os/img/7_1q.JPG"></p>
<p>которое по-умолчанию у меня в системе равно 1035</p>
<img src="../03-sysadmin-04-os/img/7_2q.JPG">
