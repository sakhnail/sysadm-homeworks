<p>1. Сценарии использования docker:</p>

- Высоконагруженное монолитное java веб-приложение: для него лучше использовать виртуальную или физическую машину, так как приложение высоконагруженное;
- Go-микросервис для генерации отчетов: лучше использовать docker, это микросервис;
- Nodejs веб-приложение: приложение статично, поэтому можно использовать docker
- Мобильное приложение c версиями для Android и iOS: если речь о backend, то лучше docker;
- База данных postgresql используемая, как кэш: все что изменяемо и чувствительно к производительности, а так же ценно, особенно БД, лучше использовать физическую машину, в крайнем случае виртуальную.
- Шина данных на базе Apache Kafka: лучше использовать виртуальную машину, хотя, наверно, можно скомбинировать VM+Docker;
- Очередь для Logstash на базе Redis: данные изменяемые и в случае падения контейнера можно часть потерять, думаю лучше использовать VM;
- Elastic stack для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana: думаю все можно распихать по контейнерам;
- Mongodb, как основное хранилище данных для java-приложения: или физическую или виртуальную машину;
- Jenkins-сервер: можно использовать docker.

<p>2. Скачал и установил докер. За'pull'ил образ httd и запустил контейнер:</p>
<p><code>docker run -p 8100:80 c8ca530172a8</code></p> <p>но не смог приаттачить свой index.html, поэтому в GUI докера при запуске контейнера примоунил папку к контейнеру у себя на компе C:/tmp в директорию /win/tmp, в нее положил свой index.html</p>
<img src="./img/dicker1.JPG">
<p>Далее написал свой Dockerfile</p>

```editorconfig
FROM httpd:latest
cp /win/tmp/index.html /usr/local/apache2/htdocs/index.html
```
<p>пытаюсь сделать <code>docker build c:/tmp/</code>, получаю</p>

```shell
[+] Building 0.0s (2/2) FINISHED
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 2B                                                                                 0.0s
 => CANCELED [internal] load .dockerignore                                                                         0.0s
 => => transferring context:                                                                                       0.0s
failed to solve with frontend dockerfile.v0: failed to read dockerfile: open /var/lib/docker/tmp/buildkit-mount733594562/Dockerfile: no such file or directory
```
и он не появляется в списке образов

<img src="./img/dicker2.JPG">