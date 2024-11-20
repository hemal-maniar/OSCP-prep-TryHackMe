##### nmap
```bash
sudo nmap -sC -sV 10.10.83.245 -oA nmap -v
```
```
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 dc:66:89:85:e7:05:c2:a5:da:7f:01:20:3a:13:fc:27 (RSA)
|   256 c3:67:dd:26:fa:0c:56:92:f3:5b:a0:b3:8d:6d:20:ab (ECDSA)
|_  256 11:9b:5a:d6:ff:2f:e4:49:d2:b5:17:36:0e:2f:1d:2f (ED25519)
8081/tcp open  http    Node.js Express framework
|_http-title: Site doesn't have a title (text/html; charset=utf-8).
|_http-cors: HEAD GET POST PUT DELETE PATCH
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
```
All port scan (fast port scan)
```bash
sudo nmap -sS -Pn -T5 -p- 10.10.83.245 -v -oA nmap2
```
```
PORT      STATE SERVICE VERSION
21/tcp    open  ftp     vsftpd 3.0.3
22/tcp    open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 dc:66:89:85:e7:05:c2:a5:da:7f:01:20:3a:13:fc:27 (RSA)
|   256 c3:67:dd:26:fa:0c:56:92:f3:5b:a0:b3:8d:6d:20:ab (ECDSA)
|_  256 11:9b:5a:d6:ff:2f:e4:49:d2:b5:17:36:0e:2f:1d:2f (ED25519)
8081/tcp  open  http    Node.js Express framework
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Site doesn't have a title (text/html; charset=utf-8).
|_http-cors: HEAD GET POST PUT DELETE PATCH
31331/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
| http-methods: 
|_  Supported Methods: POST OPTIONS HEAD GET
|_http-title: UltraTech - The best of technology (AI, FinTech, Big Data)
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-favicon: Unknown favicon MD5: 15C1B7515662078EF4B5C724E2927A96
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
```

On http://10.10.83.245:31331, found `robots.txt` pointing to sitemap
![[Pasted image 20240822134227.png]]
`/partners.html`
![[Pasted image 20240822134245.png]]
contains a log in page that uses `/auth` API for authentication. Running hydra bruteforce
```bash
hydra 10.10.83.245 -l admin -P /usr/share/wordlists/rockyou.txt -s 8081 http-get-form "/auth:login=^USER^&password=^PASS^:Invalid credentials" -t 64
```
This didn't yield anything

Looking at `/api.js` we have another endpoint /ping that pings an IP. Command injection is possible through
![[Pasted image 20240822155613.png]]
![[Pasted image 20240822155637.png]]


