<p>1. Значение C будет ошибка:TypeError: unsupported operand type(s) for +: 'int' and 'str'. Нельзя складывать разные типы переменных строчки и числа.</p>
<img src="../04-script-02-py/img/4.2.1.JPG">
<p>Необходимо переменную A изменить на строковый тип str, тогда получим значение 12</p>
<img src="../04-script-02-py/img/4.2.2.JPG">
<p>Чтобы получить значение 3, необходимо переменную B изменить на числовой тип int</p>
<img src="../04-script-02-py/img/4.2.3.JPG">
<p>2.</p>

Результат корректировки скрипта:

```python
    #!/usr/bin/env python3
    
    import os
    
    bash_command = ["cd /home/vagrant/netology/sysadm-homeworks", "git status"]
    result_os = os.popen(' && '.join(bash_command)).read()
    for result in result_os.split('\n'):
        if result.find('modified') != -1:
            prepare_result = result.replace('\tmodified:   ', '')
            print(prepare_result)

Вывод скрипта:

    vagrant@vagrant:~/netology$ ./test.py ~/netology/sysadm-homeworks/
    123
    321
    qweqweq
```
<p>3. Доработал скрипт выше так, чтобы он мог проверять не только локальный репозиторий в текущей директории, а также умел воспринимать путь к репозиторию, который мы передаём как входной параметр.</p>

```python
    #!/usr/bin/env python3

    import os
    import sys

    path_repo = sys.argv[1]
    check_dir = os.path.exists(f'{path_repo}.git')
    if check_dir != True:
        print('Данная директория не является репозиторием')
        exit()
    bash_command = [f'cd {path_repo}', "git status"]
    result_os = os.popen(' && '.join(bash_command)).read()
    for result in result_os.split('\n'):
        if result.find('modified') != -1:
            prepare_result = result.replace('\tmodified:   ', '')
            print(prepare_result)
```

Вывод скрипта:

    vagrant@vagrant:~/netology$ ./test.py ~/netology/testing1
    fatal: not a git repository (or any of the parent directories): .git

    vagrant@vagrant:~/netology$ ./test.py ~/netology/sysadm-homeworks/
    123
    321
    qweqweq

<p>4. У меня получился скрипт:</p>

````python

    import socket
    import time
    
    ip_service = {
        "drive.google.com": '',
        'mail.google.com': '',
        'google.com': ''
        }
    while True:
        for name_service, current_ip in ip_service.items():
            check_ip = socket.gethostbyname(name_service)
            time.sleep(2)
            if check_ip != current_ip:
                ip_service[name_service] = check_ip
                print(f'[ERROR] {name_service} IP mismatch: {current_ip} New IP: {check_ip}')
            else:
                print(f'{name_service} - {current_ip}')

````

Вывод скрипта:

    [ERROR] drive.google.com IP mismatch:  New IP: 173.194.73.194
    [ERROR] mail.google.com IP mismatch:  New IP: 173.194.222.83
    [ERROR] google.com IP mismatch:  New IP: 64.233.162.102
    drive.google.com - 173.194.73.194
    mail.google.com - 173.194.222.83
    google.com - 64.233.162.102
    drive.google.com - 173.194.73.194
    mail.google.com - 173.194.222.83
    [ERROR] google.com IP mismatch: 64.233.162.102 New IP: 64.233.165.100
    drive.google.com - 173.194.73.194
    mail.google.com - 173.194.222.83
    google.com - 64.233.165.100
    drive.google.com - 173.194.73.194
    [ERROR] mail.google.com IP mismatch: 173.194.222.83 New IP: 64.233.165.17
    google.com - 64.233.165.100
    drive.google.com - 173.194.73.194
    mail.google.com - 64.233.165.17
    google.com - 64.233.165.100