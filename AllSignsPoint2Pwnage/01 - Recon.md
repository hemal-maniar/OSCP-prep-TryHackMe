##### nmap
```bash
sudo nmap -sC -sV 10.10.109.161 -oA nmap -v -Pn
```
```
PORT     STATE SERVICE        VERSION
21/tcp   open  ftp            Microsoft ftpd
| ftp-syst: 
|_  SYST: Windows_NT
80/tcp   open  http           Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.11)
135/tcp  open  msrpc          Microsoft Windows RPC
139/tcp  open  netbios-ssn    Microsoft Windows netbios-ssn
443/tcp  open  ssl/http       Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.11)
| ssl-cert: Subject: commonName=localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2009-11-10T23:48:47
| Not valid after:  2019-11-08T23:48:47
| MD5:   a0a4:4cc9:9e84:b26f:9e63:9f9e:d229:dee0
|_SHA-1: b023:8c54:7a90:5bfa:119c:4e8b:acca:eacf:3649:1ff6
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1g PHP/7.4.11
445/tcp  open  microsoft-ds?
3389/tcp open  ms-wbt-server?
| ssl-cert: Subject: commonName=DESKTOP-997GG7D
| Issuer: commonName=DESKTOP-997GG7D
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2024-08-19T13:03:35
| Not valid after:  2025-02-18T13:03:35
| MD5:   b92b:d09b:55f5:fb30:36f2:dc25:c0d0:cfc6
|_SHA-1: e9de:1a0e:23b2:ba14:d1c0:a5d5:2aaa:29c2:1979:1b19
5900/tcp open  vnc            VNC (protocol 3.8)
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2024-08-20T13:21:36
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
```

All ports
```
PORT      STATE SERVICE       VERSION
21/tcp    open  ftp           Microsoft ftpd
80/tcp    open  http          Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.11)
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
443/tcp   open  ssl/http      Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.11)
445/tcp   open  microsoft-ds?
3389/tcp  open  ms-wbt-server Microsoft Terminal Services
5040/tcp  open  unknown
5900/tcp  open  vnc           VNC (protocol 3.8)
49664/tcp open  msrpc         Microsoft Windows RPC
49665/tcp open  msrpc         Microsoft Windows RPC
49666/tcp open  msrpc         Microsoft Windows RPC
49667/tcp open  msrpc         Microsoft Windows RPC
49668/tcp open  msrpc         Microsoft Windows RPC
49679/tcp open  msrpc         Microsoft Windows RPC
49682/tcp open  msrpc         Microsoft Windows RPC
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```
##### smbclient
```bash
smbclient -N -L \\10.10.109.161
```
![[Pasted image 20240820170507.png]]

on the webserver, adding files to /images$ share can be accessed via the website. The website is running `content.php` file that fetches image and displays it. 