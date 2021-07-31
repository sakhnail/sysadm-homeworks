<p>1. Исправил скрипт (добавил кавычки):
"info" : "Sample JSON output from our service\t",
    "elements" :[
        { "name" : "first",
        "type" : "server",
        "ip" : 7175 
        },
        { "name" : "second",
        "type" : "proxy",
        "ip" : "71.78.22.43"
        }
    ]
}</code></pre></p>
<p>2. Скрипт:</p>
<pre><code>import socket
import time
import json
import yaml

ip_service = {
    "drive.google.com": '',
    'mail.google.com': '',
    'google.com': ''
    }
while True:
    for name_service, current_ip in ip_service.items():
        check_ip = socket.gethostbyname(name_service)
        time.sleep(1)
        if check_ip != current_ip:
            ip_service[name_service] = check_ip
            with open("tes1.json", 'w') as js_f, open("test.yml", 'w') as ym_f:
                js_f.write(json.dumps(ip_service, indent=2))
                ym_f.write(yaml.dump(ip_service))
            print(f'[ERROR] {name_service} IP mismatch: {current_ip} New IP: {check_ip}')
        else:
            print(f'{name_service} - {current_ip}')
</code></pre>
