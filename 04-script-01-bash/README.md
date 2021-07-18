<p>1. <em>с</em> будет равно <em>a+b</em>, так как не были задекларированы все переменные, поэтому отображаются как строки, <em>d</em> будет равно <em>1+2</em>, так как показывает значение a и b, <em>e</em> будет равно <em>3</em></p>
<img src="../04-script-01-bash/img/bh1.JPG">
<p>2. В скрипте: 
<pre><code>while ((1==1)  		# здесь не хватает второй скобки
    do
    curl https://localhost:4757
if (($? != 0))
then  			    #необходимо добавить break
    date >> curl.log    #чтобы не заканчивалось место, надо не добавить запись в конец лога, а внести новую
fi			
done</code></pre></p>
<p>Чтобы он правильно отрабатывал, необходимо внести следующие правки:</p>
<pre><code>while ((1==1))
    do
    curl https://localhost:4757
if (($? != 0))
then  			
    date > curl.log
else
    break
fi			
done</code></pre>
<p>3. Скрипт, который проверяет доступность трёх IP: 192.168.0.1, 173.194.222.113, 87.250.250.242 по 80 порту и записывает результат в файл log:</p>
<pre><code>#!/bin/bash

for ((i=1; i<5; i++))
    do 
while ((1==1))
    do
    curl 192.168.0.1:80
    curl 173.194.222.113:80 
    curl 87.250.250.242:80
if (($? != 0))
then
    date > curl.log
fi
done
done</code></pre>
<p>версия скрипта, где он выполнялся до тех пор, пока один из узлов не окажется недоступным и пишет ошибки в error-лог</p>
<pre><code>#!/bin/bash

for ((i=1; i<5; i++))
    do 
while ((1==1))
    do
    curl 192.168.0.1:80
    curl 173.194.222.113:80 
    curl 87.250.250.242:80
if (($? != 0))
then
    date > curl.log
else
    echo "error"
fi
done
done</code></pre>