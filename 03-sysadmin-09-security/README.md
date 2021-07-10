<p>1. Добавил в Vagrantfile виртуальной машины конфиг <code>config.vm.network "forwarded_port", guest: 8200, host: 8200</code></p>
<img src="../03-sysadmin-09-security/img/sec9.JPG">
<p>2. Vault-сервер в dev-режиме</p>
<img src="../03-sysadmin-09-security/img/sec91.JPG">
<p>Добавил переменную для взаимодействия с сервером и значение <code>VAULT_TOKEN</code></p>
<img src="../03-sysadmin-09-security/img/sec92.JPG">
<p>3. Cоздал Root CA и Intermediate CA</p>
<img src="../03-sysadmin-09-security/img/sec93.JPG">