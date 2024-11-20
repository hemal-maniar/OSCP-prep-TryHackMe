##### nmap
```bash
sudo nmap -sC -sV 10.10.13.251 -oA nmap -v
```
```
PORT      STATE SERVICE VERSION
21/tcp    open  ftp     vsftpd 3.0.3
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.11.103.8
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp    open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
| http-robots.txt: 1 disallowed entry 
|_/
|_http-title: Apache2 Ubuntu Default Page: It works
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
10000/tcp open  http    MiniServ 1.930 (Webmin httpd)
|_http-favicon: Unknown favicon MD5: D7262463815A31BC33FB136C11104B03
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Site doesn't have a title (text/html; Charset=iso-8859-1).
Service Info: OS: Unix
```
All port scan
```
55007/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
```

##### FTP
Anonymous FTP login is allowed
```bash
ftp 10.10.13.251
```
```
ftp> anonymous
ftp> ls -la
... .info.txt
ftp> get .info.txt
```

`Whfg jnagrq gb frr vs lbh svaq vg. Yby. Erzrzore: Rahzrengvba vf gur xrl!`

- Looks like this is ciphered. 
- Identified it to be a ROT-13 cipher
`Just wanted to see if you find it. Lol. Remember: Enumeration is the key!`

It just says `enumeration is the key!`. Nothing of importance here

##### Webserver

robots.txt:
![[Pasted image 20240821170008.png]]

the website is also running Joomla CMS

More enumeration gives a directory `/joomla/_test/` with sar2html
Found an RCE for sar2html ([ExploitDB](https://www.exploit-db.com/exploits/47204))
![[Pasted image 20240821172126.png]]
![[Pasted image 20240821172306.png]]
The output is shown in the dropdown where we can see current user as `www-data`
![[Pasted image 20240821174229.png]]

Found an entry in `log.txt` for user `basterd:superduperp@$$`