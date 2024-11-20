##### nmap

All port scan
```bash
sudo nmap -sS -Pn -T5 -p- 10.10.94.13 -oA nmap2 -v
```
```
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
8009/tcp open  ajp13
8080/tcp open  http-proxy
```

```bash
sudo nmap -sC -sV 10.10.94.13 -p 22,53,8009,8080 -v -oA nmap
```
```
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 f3:c8:9f:0b:6a:c5:fe:95:54:0b:e9:e3:ba:93:db:7c (RSA)
|   256 dd:1a:09:f5:99:63:a3:43:0d:2d:90:d8:e3:e1:1f:b9 (ECDSA)
|_  256 48:d1:30:1b:38:6c:c6:53:ea:30:81:80:5d:0c:f1:05 (ED25519)
53/tcp   open  tcpwrapped
8009/tcp open  ajp13      Apache Jserv (Protocol v1.3)
| ajp-methods: 
|_  Supported methods: GET HEAD POST OPTIONS
8080/tcp open  http       Apache Tomcat 9.0.30
|_http-favicon: Apache Tomcat
|_http-title: Apache Tomcat/9.0.30
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

Navigated to http://10.01.94.13:8080 running Apache Tomcat 9.0.30
![[Pasted image 20240823181334.png]]

- Found a file inclusion vulnerability that shows content of files within the web directory
- Following the instruction on [GitHub](https://github.com/Hancheng-Lei/Hacking-Vulnerability-CVE-2020-1938-Ghostcat/blob/main/CVE-2020-1938.md)
- we can read contents of WEB-INF/web.xml 
![[Pasted image 20240823181451.png]]
`skyfuck:8730281lkjlkjdqlksalks`