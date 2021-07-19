<p>1. Добавил в Vagrantfile виртуальной машины конфиг <code>config.vm.network "forwarded_port", guest: 8200, host: 8200</code></p>
<img src="../03-sysadmin-09-security/img/sec9.JPG">
<p>2. Vault-сервер в dev-режиме</p>
<img src="../03-sysadmin-09-security/img/sec91.JPG">
<p>Добавил переменную для взаимодействия с сервером и значение <code>VAULT_TOKEN</code></p>
<img src="../03-sysadmin-09-security/img/sec92.JPG">
<p>3. Cоздал Root CA и Intermediate CA</p>
<img src="../03-sysadmin-09-security/img/sec93.JPG">
<p>а так же сертификаты для netology.example.com</p>
<img src="../03-sysadmin-09-security/img/sec94.JPG">
<p>5. Установил и настроил как службу nginx на работу с SSL сертификатами</p>
<img src="../03-sysadmin-09-security/img/sec95.JPG">
<p>Дальше не совсем понимаю, откуда взять сертификаты, чтобы подцепить их в nginx</p>