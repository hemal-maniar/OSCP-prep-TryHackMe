##### nmap
```bash
sudo nmap -sC -sV 10.10.89.126 -oA nmap -Pn -v
```
```
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS httpd 10.0
|_http-server-header: Microsoft-IIS/10.0
|_http-title: IIS Windows Server
| http-methods: 
|   Supported Methods: OPTIONS TRACE GET HEAD POST
|_  Potentially risky methods: TRACE
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: RETROWEB
|   NetBIOS_Domain_Name: RETROWEB
|   NetBIOS_Computer_Name: RETROWEB
|   DNS_Domain_Name: RetroWeb
|   DNS_Computer_Name: RetroWeb
|   Product_Version: 10.0.14393
|_  System_Time: 2024-08-14T08:09:01+00:00
| ssl-cert: Subject: commonName=RetroWeb
| Issuer: commonName=RetroWeb
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2024-08-13T08:03:25
| Not valid after:  2025-02-12T08:03:25
| MD5:   e46a:011e:70f8:df78:a847:56f0:b34d:8709
|_SHA-1: 2454:d168:b905:6f8b:5fed:b418:5162:3afb:dd00:e84d
|_ssl-date: 2024-08-14T08:09:05+00:00; -1s from scanner time.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

Found a blog post on
`http://10.10.46.78/retro/index.php/2019/12/09/ready-player-one/`
![[Pasted image 20240815145118.png]]
![[Pasted image 20240815145128.png]]

Gathered credentials for user `Wade:parzival`