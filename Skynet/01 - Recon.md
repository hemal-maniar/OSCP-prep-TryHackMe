##### nmap

Running all port discovery
```bash
sudo nmap -sS -Pn -T5 -p- 10.10.220.13 -v -oA nmap2
```
```
PORT      STATE    SERVICE
22/tcp    open     ssh
80/tcp    open     http
110/tcp   open     pop3
139/tcp   open     netbios-ssn
143/tcp   open     imap
445/tcp   open     microsoft-ds
691/tcp   filtered resvc
46134/tcp filtered unknown
61864/tcp filtered unknown
```

```bash
sudo nmap -sC -sV 10.10.220.13 -p 22,80,110,139,143,445,691,46134,61864 -v -oA nmap
```
```
PORT      STATE  SERVICE     VERSION
22/tcp    open   ssh         OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 99:23:31:bb:b1:e9:43:b7:56:94:4c:b9:e8:21:46:c5 (RSA)
|   256 57:c0:75:02:71:2d:19:31:83:db:e4:fe:67:96:68:cf (ECDSA)
|_  256 46:fa:4e:fc:10:a5:4f:57:57:d0:6d:54:f6:c3:4d:fe (ED25519)
80/tcp    open   http        Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Skynet
| http-methods: 
|_  Supported Methods: GET HEAD POST OPTIONS
|_http-server-header: Apache/2.4.18 (Ubuntu)
110/tcp   open   pop3        Dovecot pop3d
|_pop3-capabilities: UIDL CAPA PIPELINING SASL RESP-CODES AUTH-RESP-CODE TOP
139/tcp   open   netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
143/tcp   open   imap        Dovecot imapd
|_imap-capabilities: IDLE more have LITERAL+ ENABLE LOGIN-REFERRALS ID listed SASL-IR Pre-login IMAP4rev1 OK LOGINDISABLEDA0001 post-login capabilities
445/tcp   open   netbios-ssn Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)
691/tcp   closed resvc
46134/tcp closed unknown
61864/tcp closed unknown
Service Info: Host: SKYNET; OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb-os-discovery: 
|   OS: Windows 6.1 (Samba 4.3.11-Ubuntu)
|   Computer name: skynet
|   NetBIOS computer name: SKYNET\x00
|   Domain name: \x00
|   FQDN: skynet
|_  System time: 2024-08-22T09:40:54-05:00
|_clock-skew: mean: 1h40m00s, deviation: 2h53m12s, median: 0s
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
| nbstat: NetBIOS name: SKYNET, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
| Names:
|   SKYNET<00>           Flags: <unique><active>
|   SKYNET<03>           Flags: <unique><active>
|   SKYNET<20>           Flags: <unique><active>
|   \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|   WORKGROUP<00>        Flags: <group><active>
|   WORKGROUP<1d>        Flags: <unique><active>
|_  WORKGROUP<1e>        Flags: <group><active>
| smb2-time: 
|   date: 2024-08-22T14:40:54
|_  start_date: N/A
```

##### smbclient
```bash
smbclient -N -L \\10.10.220.13
```
![[Pasted image 20240822184333.png]]

\\\\anonymous
- Found a text file `attention.txt` which tells us that all users passwords have been reset. Author is Miles Dyson
- Found a file with wordlist `log1.txt

Directory enumeration revealed squirrelmail 1.4.23 running on the webserver