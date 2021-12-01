1. Установил ansible 2.10
<p>Создал репозиторий: https://github.com/sakhnail/ansible</p>
<p>Скачал playbook в свой репозиторий</p>
2. Запустил playbook

![img.png](img.png)

Заменил <code>some_fact:</code> в group_vars/all/examp.yml <code>some_fact: "all default fact"</code>

![img_1.png](img_1.png)

Запустил докер-контейнеры и запуск playbook на окружении prod.yml 

![img_2.png](img_2.png)

Изменил факты в <code>group_vars/deb/examp.yml</code> и <code>group_vars/el/examp.yml</code>
Проверил playbook на prod.yml

![img_3.png](img_3.png)

Зашифровал факты в group_vars/deb и group_vars/el

![img_5.png](img_5.png)

Запуск prod с запросом пароля

![img_6.png](img_6.png)

Вывод ansible-doc

![img_7.png](img_7.png)

*Наверно нужен "local"

Добавил local в prod

![img_8.png](img_8.png)

Запустил playbook на окружении prod.yml

![img_9.png](img_9.png)